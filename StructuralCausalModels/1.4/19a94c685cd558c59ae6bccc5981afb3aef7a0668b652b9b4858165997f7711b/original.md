# `set_dag_df!`

Set or update Dataframe associated to DAG

```julia
set_dag_df!(d, df; force)

```

### Required arguments

```julia
* `d::DAG`                                  : Previously defined DAG object 
* `df::DataFrameOrNothing`                  : DataFrame associated with DAG
)
```

### Optional arguments

```julia
* `force=false`                             : Force assignment of df 
)
```

The `force = true` option can be used if the DAG involves unobserved nodes.

Part of API, exported.
