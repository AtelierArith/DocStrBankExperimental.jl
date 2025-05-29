```
@with(ctx..., body)
```

コンテキスト `ctx` を使用して `body` を計算します。`ctx` は通常、名前付きタプルですが、唯一の要件は `Base.getproperty` をサポートしていることです。

このマクロは、`body` の型レベルの表現を作成し、これを型に基づいてディスパッチする「一般化された生成」関数に渡すことによって機能します。名前付きタプルのデフォルトがあります：

```
julia> nt = (x=2, y=3)
(x = 2, y = 3)

julia> @with nt begin
       x^2 + y
       end
7
```

これは他の型や異なる数の引数に拡張できます。例えば、

```
julia> using NestedTuples: with

julia> NestedTuples.with(nt1, nt2, ex) = with(nt1, ex) + with(nt2, ex)

julia> @with nt nt begin
       x^2 + y
       end
14
```

または 

```
julia> NestedTuples.with(nt1, v::Vector, ex) = with(nt1, ex) .+ v

julia> @with nt [1,2,3] begin
       x^2 + y
       end
3-element Vector{Int64}:
  8
  9
 10
```
