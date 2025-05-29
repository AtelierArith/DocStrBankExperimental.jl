```
@dumpct <expression>
```

Dump the expression at compile-time.

# Examples

```jldoctest
julia> function foo(x)
           @dumpct :x + x + $x
           x
       end
Expr
  head: Symbol call
  args: Array{Any}((4,))
    1: Symbol +
    2: QuoteNode
      value: Symbol x
    3: Symbol x
    4: Expr
      head: Symbol $
      args: Array{Any}((1,))
        1: Symbol x
foo (generic function with 1 method)

julia> foo(42)
42
```
