```
select_bind_input(type, name; value, select, bind_options...)
```

Convenient function to create a `ParamsSpec` with the following structure:

```json
{
  "name": name,
  "value": value,
  "select": select,
  "bind": {
    "input": type,
    bind_options...
  }
}
```
