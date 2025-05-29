```
create_database(ctx, name::String[, source::String])
```

Create a database with the specified `name`, optionally cloning from an existing `source`. NOTE: It is an error (`HTTPError(400)`) to create a database that already exists. To overwrite a database, you must first `delete_database(ctx, name)`, then create it.
