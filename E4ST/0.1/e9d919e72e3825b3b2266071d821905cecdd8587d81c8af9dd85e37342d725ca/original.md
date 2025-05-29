```
setup_table!(config, data, ::Val{:gen})
```

Sets up the generator table. Creates potential new generators and exogenously built generators.  Calls [`append_builds!`](@ref) Creates age column which is a ByYear column. Unbuilt generators have a negative age before year_on.
