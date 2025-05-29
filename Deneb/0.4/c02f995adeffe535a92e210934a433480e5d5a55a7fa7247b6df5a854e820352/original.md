```
select(type, name; value, bind, select_options...)
```

Convenient function to create a `ParamsSpec` with the following structure:

```json
{
  "name": name,
  "value": value,
  "select": {
    "type": type,
    select_options...
  },
  "bind": bind
}
```
