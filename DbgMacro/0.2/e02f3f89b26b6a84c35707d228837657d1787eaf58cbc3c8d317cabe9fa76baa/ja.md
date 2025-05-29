```
@dumprt <expression>
```

実行時に式をダンプします。

# 例

```jldoctest
julia> function foo(x)
           @dumprt :x + x + $x
           x
       end
foo (generic function with 1 method)

julia> foo(42)
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
42
```
