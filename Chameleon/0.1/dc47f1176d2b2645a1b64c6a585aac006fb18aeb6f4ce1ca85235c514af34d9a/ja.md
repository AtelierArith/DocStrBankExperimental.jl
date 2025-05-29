```
distinct_colors(
    n_colors::Integer;
    minimal_saturation::Real=33,
    minimal_lightness::Real=20,
    maximal_lightness::Real=80
)::Tuple{AbstractVector{<:AbstractString}, AbstractMatrix{<:Real}}
```

異なる色の数を選択します。

これは、必要な数の球体を使用してCIELAB色空間の（可視部分）をパッキングすることによって、すべての色が異なることを保証し、それらの中心を使用して色を生成します。

# 引数

  * `n_colors`: 要求される（正の）色の数。
  * `minimal_saturation`: この値未満の彩度（CIELAB色空間におけるhypot(a, b））を持つ色を除外します。
  * `minimal_lightness`: この値未満の明度（CIELAB色空間におけるl）を持つ色を除外します。
  * `maximal_lightness=80`: この値を超える明度（CIELAB色空間におけるl）を持つ色を除外します。

# 戻り値

色の名前のベクトルと色の`lab`座標の行列を含むタプル（行は`l`、`a`、`b`、列は色）。色は通常の`#RRGGBB`16進数形式で名前付けされています。
