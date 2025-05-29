```
NamedTupleExpr(args::Vector{NamedTupleArg})
NamedTupleExpr(; args::Vector{NamedTupleArg})
```

Matches a (named) tuple expression

The `key`s and `value`s of this expression can be accessed, modified, and queried with `Base.getindex`, `Base.setindex!`, `Base.iterate`, `Base.findfirst`, `Base.keys`, `Base.haskey`, `Base.length`, `Base.pop!`, and `Base.push!`
