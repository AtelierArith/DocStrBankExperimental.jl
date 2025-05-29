```
use(db::Surreal; namespace::String, database::String)
```

Switch to a specific namespace and database.

# Arguments

  * `namespace`: Switches to a specific namespace.
  * `database`: Switches to a specific database.

# Examples

```jldoctest
julia> use(db, namespace='test', database='test')
```
