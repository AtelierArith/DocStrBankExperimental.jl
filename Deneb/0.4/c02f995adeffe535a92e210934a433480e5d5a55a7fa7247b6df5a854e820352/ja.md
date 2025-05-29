```
select(type, name; value, bind, select_options...)
```

次の構造を持つ `ParamsSpec` を作成する便利な関数：

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
