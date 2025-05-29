```
perlin_2d(; seed=nothing)
perlin_improved_2d(; seed=nothing)
```

2次元のPerlin "Improved" ノイズをサンプリングするサンプラーを構築します。

# 引数

  * `seed`: このサンプラーの乱数生成器をシードするために使用される符号なし整数、または非決定的な結果のための `nothing`。

# 注意事項:

  * `perlin_improved_2d` は非推奨であり、将来のメジャーバージョンリリースで `perlin_2d` に置き換えられます。
