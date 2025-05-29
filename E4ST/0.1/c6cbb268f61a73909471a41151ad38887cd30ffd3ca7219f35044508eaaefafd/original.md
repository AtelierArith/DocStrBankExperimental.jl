```
setup_table!(config, data, table_name)
```

Sets up the `data[:table_name]`.  Calls `setup_table!(config, data, Val(table_name))`, if defined.
