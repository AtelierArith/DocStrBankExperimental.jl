```
pretty_table_with_conf(conf::PrettyTablesConf, args...; kwargs...) -> Nothing
```

Call `pretty_table` using the default configuration in `conf`. The `args...` and `kwargs...` can be the same as those passed to `pretty_tables`. Notice that all the configurations in `kwargs...` will overwrite the ones in `conf`.

The object `conf` can be created by the function `set_pt_conf` in which the keyword parameters can be any one supported by the function `pretty_table` as shown in the following.
