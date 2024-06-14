
# Spring Data Rest


Spring Data REST is a Spring project that simplifies the development of RESTful services by automatically exposing CRUD (Create, Read, Update, Delete) operations for Spring Data repositories as RESTful endpoints.

Spring Data Rest helps to expose our Jpa repository as rest Api.

    RestController + JpaRepository = RestRepositoryResource

Steps to implement spring Data Rest concept in spring boot project

1) Create Spring starter project with below dependencies

		a) rest-repositories (data-rest)
		b) data-jpa
		c) mysql-connector-j
		d) devtools

2) Configure datasource properties 

3) Create Entity class for table mapping

@Entity
@Table(name = "book_tbl")
public class Book {

	@Id
	private Integer id;
	private String name;
    private Double price;

}

4) Create Rest Repository to expose REST API methods
 
    @RepositoryRestResource(path = "books")
    public interface BookRepository extends JpaRepository<Book,    Integer>{

    public List<Book> findByName(@Param("name") String name);
}
