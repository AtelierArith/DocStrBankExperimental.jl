# `set_dag_cov_matrix!`

Set or update the covariance matrix associated to DAG

```julia
set_dag_cov_matrix!(d, cm; force)

```

### Required arguments

```julia
* `d::DAG`                                  : Previously defined DAG object 
* `cm::NamedArrayOrNothing`                 : Covariance matrix in NamedArray format
)
```

### Optional arguments

```julia
* `force=false`                             : Force assignment of df 
)
```

The `force = true` option can be used if the DAG involves unobserved nodes.

Part of API, exported.
