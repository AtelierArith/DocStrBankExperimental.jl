```
waterheight(q, equations)
```

与えられた `equations` のセットに対して、原始変数 `q` の水深を返します。すなわち、底質の上の水深 $h$ です。

`q` は単一のノードでの原始変数のベクトルであり、すなわち正しい長さ `nvariables(equations)` のベクトルです。

他にも [`waterheight_total`](@ref)、[`bathymetry`](@ref) を参照してください。
