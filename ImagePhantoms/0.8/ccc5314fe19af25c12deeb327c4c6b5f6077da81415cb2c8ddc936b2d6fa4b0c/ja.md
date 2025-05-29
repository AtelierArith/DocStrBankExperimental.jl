```
focus_chart( ; radius=1, nspoke=30, value=1)
```

フォーカスチャートのための `nspoke` 三角形ファントムパラメータを生成します。`phantom` に渡すための `Vector{Object2d{Triangle}` を返します。

# オプション

  * `radius::RealU = 1` ファントムの半径
  * `nspoke::Int = 60` スポークの数
  * `value::Number = 1` 0とこの値の間で交互に切り替えます
