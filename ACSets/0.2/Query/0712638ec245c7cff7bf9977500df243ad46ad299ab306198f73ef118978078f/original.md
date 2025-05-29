AbstractQueryFormatter

Concrete, fieldless structs which are subtypes of AbstractQueryFormatter should have a callable method which ingests a ACSetSQLNode, an ACSet, and the `selected`, the result of the query subject to the given ACSetSQL Select statements.

For example, the standard format for ACSetSQL output is

```
struct SimpleQueryFormatter <: AbstractQueryFormatter end

(qf::SimpleQueryFormatter)(q, a, s) = s

```

See also [`SimpleQueryFormatter`](@ref), [`NamedQueryFormatter`](@ref), [`DFQueryFormatter`](@ref).
