```
Constant{N} <: Real
```

コンパイル時に既知の値を持つ数値フィールド定数 `N`。

```Julia
julia> Constant(100)
100
```

`Constant` に対する演算は閉じており（`*`、`/`、`+`、`-`、`^`）、非 `Constant` 引数と混合されると `Float64` 値のように振る舞います。
