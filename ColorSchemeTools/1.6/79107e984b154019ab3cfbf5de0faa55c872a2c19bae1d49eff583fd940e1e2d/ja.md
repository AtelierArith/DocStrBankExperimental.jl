```
equalize(cs::ColorScheme;
    colormodel::Symbol="RGB",
    formula::String="CIE76",
    W::Array=[1.0, 0.0, 0.0],
    sigma::Real=0.0,
    cyclic::Bool=false)

equalize(ca::Array{Colorant, 1}; 
    # same keywords 
    )
```

カラー スキーム `cs` または色の配列 `ca` の色を均一に知覚できるように調整します。

  * `cs` は ColorScheme です
  * `ca` は色の配列です
  * `colormodel` は `:RGB` または `:LAB` です
  * `formula` は "CIE76" または "CIEDE2000" です
  * `W` は明度、彩度、色相成分の差分方程式に適用される三つの重みのベクトルです
  * `sigma` はオプションのガウス平滑化パラメータです
  * `cyclic` はカラーマップが周期的であるかどうかを示すブールフラグです

調整された色を持つカラー スキームを返します。
