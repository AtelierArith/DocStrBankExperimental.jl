```
perlin_1d(; seed=nothing)
perlin_improved_1d(; seed=nothing)
```

1次元のPerlin「改善された」ノイズをサンプリングすると出力するサンプラーを構築します。

# 引数

  * `seed`: このサンプラーの乱数生成器をシードするために使用される符号なし整数、または非決定的な結果のための`nothing`。

# 注意事項:

  * `perlin_improved_1d`は非推奨であり、将来のメジャーバージョンリリースで`perlin_1d`に置き換えられます。
  * この関数を品質の高いノイズに使用しないことを*強く*推奨します。結果は非常に規則的になります。この問題に対抗するために人々が行った多くのトリックがありますが、それらはすべて負担に見合わないトレードオフがあります。

    推奨される代替手段は、[`simplex_1d`](@ref simplex_1d)を使用するか、[`perlin_3d`](@ref perlin_3d)を使用して2つの座標を固定し、`0.0`、`0.5`、または`1.0`に近くないようにすることです。
