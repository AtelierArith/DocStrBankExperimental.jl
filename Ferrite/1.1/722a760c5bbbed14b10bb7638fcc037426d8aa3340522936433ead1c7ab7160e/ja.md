```
addcellset!(grid::AbstractGrid, name::String, cellid::AbstractVecOrSet{Int})
addcellset!(grid::AbstractGrid, name::String, f::function; all::Bool=true)
```

グリッドにキー `name` を持つセルセットを追加します。セルセットは通常、問題のサブドメインを定義するために使用されます。例えば、計算領域内の2つの材料などです。`DofHandler` は、全体のドメインではなく、セルセット上に存在する異なるフィールドを構築できます。`all=true` は、セルがセットに追加されるべき場合、`f(x)` がセル内のすべてのノード座標 `x` に対して `true` を返す必要があることを意味します。そうでない場合、`f(x)` が1つのノードに対して `true` を返すだけで十分です。

```julia
addcellset!(grid, "left", Set((1,3))) #id 1と3のセルをセルセットleftに追加
addcellset!(grid, "right", x -> norm(x[1]) < 2.0 ) #各セルのノードのx[1]が2.0未満であればセルをセルセットrightに追加
```
