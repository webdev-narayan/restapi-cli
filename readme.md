# restapi-cli

restapi-cli is a command-line tool designed to simplify the process of building APIs by generating boilerplate code quickly and easily.

## Installation

To use restapi-cli, simply install it globally via npm:

```bash
npm install restapi-cli
```

## Usage

### Initializing restapi-cli

To initialize restapi-cli in your project, run the following command:

```bash
restapi-cli init
```

This command will create a `cli.config.js` file in your project directory with the following content:

```javascript
export default {
    "apiPath": "src/api",
    "databasePath": "database/index.js",
    "orm": "sequelize",
};
```

You can customize the configuration according to your project needs. Available options for `orm` are "sequelize" for PostgreSQL and "mongoose" for MongoDB.

### Generating APIs

To generate a new API, run the following command:

```bash
restapi-cli generate
```

This command will prompt you to enter the model name and fields. For example, if you enter `user` as the model name and `name:string,email:string` as the fields, restapi-cli will create a folder named `user` inside the specified `apiPath` with the following structure:

```
user/
|-- controllers/
|   |-- user.js
|-- models/
|   |-- user.js
|-- middlewares/
|   |-- user.js
|-- routes/
|   |-- user.js
```

The RESTful API for the `user` model is now ready to serve.

### RESTful Routes

The generated routes are fully RESTful, following best practices for REST APIs. By using restapi-cli, users can easily follow RESTful API principles and become masters of API development.

For example, for a `user` model, the generated routes might look like this:
```javascript
import { Router } from 'express';
import { create, find, update, destroy, findOne } from '../controllers/user.js';
const router = Router();

// Create user
router.post("/api/users", [], create);

// List users
router.get("/api/users", [], find);

// List Single user
router.get("/api/users/:id", [], findOne);

// Update users
router.put("/api/users/:id", [], update);

// Delete user
router.delete("/api/users/:id", [], destroy);

export default router;
```


### Removing APIs

To remove a generated API, run the following command:

```bash
restapi-cli remove modelName
```

Replace `modelName` with the name of the model you want to remove. This command will delete the corresponding folder and its contents from the specified `apiPath`.

## Support

restapi-cli currently supports generating APIs with Sequelize for PostgreSQL and Mongoose for MongoDB. If you encounter any issues or have suggestions for improvement, please feel free to open an issue on [GitHub](https://github.com/webdev-narayan/restapi-cli).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.