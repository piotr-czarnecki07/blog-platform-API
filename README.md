# blog-platform-API

RESTful API for a blogging platform service.  
Provides CRUD operations for managing blog posts.  

> [!NOTE]
> The API doesn't implement user authentication, which is why it should communicate with only one client, serving as an internal usage API for another application.

## Table of Contents
- [Technologies Used](#technologies-used)
- [Setting up the Environment](#setting-up-the-enviroment)
- [How to Use](#how-to-ues)
- [License](#license)
- [Credits](#credits)

## Technologies Used

Django REST framework was used for:
- Handling requests and responses with the client.
- Saving and retrieving data from the database.
- Connecting to an external database host.

PostgreSQL database from https://aiven.io was used for storing user posts.

## Setting up the Environment

1. Ensure Python 3.13+ is installed.
2. Create a virtual environment, for example, by running `py -m venv venv` in the Command Prompt.
3. Activate the environment.
4. Install dependencies from `requirements.txt`.
5. Create a `.env` file based on the `.env.example` in the `./BloggingPlatform/` directory. (UWAGA: ).
6. Change the Command Prompt's current working directory to the `./BloggingPlatform/` directory.
7. Run `manage.py runserver` and open the browser on the provided host.

*This steps are not necessary if the API is hosted on a public domain*

## How to Use

When the API is hosted, operations can be performed by sending proper requests to the following URLs:

- `/getById/<int:id>`  
  Returns the blog post from the database with the given ID number.  
  ID numbers are provided within the response for the `/post` operation.  
  Requires the `GET` HTTP method.

- `/getByTitle/<str:title>`  
  Returns the blog post based on its title.  
  The title must match the one provided within the `/post` method, but spaces (white characters) should be removed.  
  Requires the `GET` HTTP method.

- `/post`  
  Allows the API user to send a blog post to be saved to the database.  
  The request must contain fields like `title`, `content`, `category` (as strings), and `tags` (as a list of strings).  
  Requires the `POST` HTTP method.

- `/update/<int:id>`  
  Updates the existing blog post with the provided ID using the newly requested field values.  
  The request should contain fields similar to those in the `/post` method.  
  Requires the `PUT` HTTP method.

- `/delete/<int:id>`  
  Deletes the blog post with the provided ID.  
  Requires the `DELETE` HTTP method.

- `/getall`  
  Returns all posts available in the database.  
  Requires the `GET` HTTP method.

- `/getByTag/<str:tag>`  
  Returns all posts that contain the provided tag.  
  Requires the `GET` HTTP method.

## License

This project is licensed under the MIT License.
See [LICENSE](./LICENSE) for more information.

## Credits

- Idea: [https://roadmap.sh/projects/blogging-platform-api](https://roadmap.sh/projects/blogging-platform-api)  
- Database Host: [https://aiven.io](https://aiven.io)  
