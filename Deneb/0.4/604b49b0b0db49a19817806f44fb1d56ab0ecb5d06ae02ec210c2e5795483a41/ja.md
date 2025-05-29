```
select_bind_input(type, name; value, select, bind_options...)
```

便利な関数で、次の構造を持つ `ParamsSpec` を作成します：

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
