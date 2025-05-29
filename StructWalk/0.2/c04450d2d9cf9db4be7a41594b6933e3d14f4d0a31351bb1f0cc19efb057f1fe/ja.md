```
postwalk(f, [style = WalkStyle], x)
```

`f`を`x`の各ノードに適用し、結果を返します。`f`は最初に葉を見てから変換されたノードを見ます。

# 例

```julia-repl
julia> postwalk(x -> @show(x) isa Integer ? x + 1 : x, (a=2, b=(c=4, d=0)))
x = 2
x = 4
x = 0
x = (c = 5, d = 1)
x = (a = 3, b = (c = 5, d = 1))
(a = 3, b = (c = 5, d = 1))

julia> postwalk(x -> @show(x) isa Integer ? x + 1 : x .+ 1, (3, 5))
x = 3
x = 5
x = (4, 6)
(5, 7)

julia> postwalk(x -> @show(x) isa Integer ? x // 2 : x isa Tuple ? =>(x .+ 1...) : x, (3, 5))
x = 3
x = 5
x = (3//2, 5//2)
5//2 => 7//2

```

参照: [`prewalk`](@ref)
