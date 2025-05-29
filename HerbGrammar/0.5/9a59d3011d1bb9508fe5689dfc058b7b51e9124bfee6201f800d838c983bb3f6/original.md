```
add_rule!(g::AbstractGrammar, e::Expr)
```

Adds a rule to the grammar. 

### Usage:

```
    add_rule!(grammar, :("Real = Real + Real"))
```

The syntax is identical to the syntax of [`@csgrammar`](@ref) and [`@cfgrammar`](@ref), but only single rules are supported.

!!! warning
    Calls to this function are ignored if a rule is already in the grammar.

