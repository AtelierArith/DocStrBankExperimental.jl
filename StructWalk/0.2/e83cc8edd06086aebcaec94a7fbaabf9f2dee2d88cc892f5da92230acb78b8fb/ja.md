```
prewalk(f, [style = WalkStyle], x)
```

`f`を`x`の各ノードに適用し、結果を返します。`f`はノードを最初に見てから変換された葉を見ます。

*注意* 変換されたノードが非葉値になると無限に歩く可能性があることに注意してください。無限の歩行を防ぐために、`f`内で非葉値を`LeafNode(y)`でラップしてください。

# 例

```julia-repl
julia> prewalk(x -> @show(x) isa Integer ? x + 1 : x, (a=2, b=(c=4, d=0)))
x = (a = 2, b = (c = 4, d = 0))
x = 2
x = (c = 4, d = 0)
x = 4
x = 0
(a = 3, b = (c = 5, d = 1))

julia> prewalk(x -> @show(x) isa Integer ? x + 1 : x .+ 1, (3, 5))
x = (3, 5)
x = 4
x = 6
(5, 7)

julia> prewalk(x -> @show(x) isa Integer ? StructWalk.LeafNode(x // 2) : x isa Tuple ? =>(x .+ 1...) : x, (3, 5))
x = (3, 5)
x = 4
x = 6
2//1 => 3//1

```

参照: [`postwalk`](@ref), [`LeafNode`](@ref)
