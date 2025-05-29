```
DGMulti(; polydeg::Integer,
          element_type::AbstractElemShape,
          approximation_type=Polynomial(),
          surface_flux=flux_central,
          surface_integral=SurfaceIntegralWeakForm(surface_flux),
          volume_integral=VolumeIntegralWeakForm(),
          RefElemData_kwargs...)
```

不連続ガレルキン法を作成します。

  * 多項式次数 `polydeg` の近似
  * 要素タイプ `element_type` （現在サポートされているのは `Tri()`、`Quad()`、`Tet()`、`Hex()`）

オプション:

  * `approximation_type` （デフォルトは `Polynomial()`; `SBP()` も `Tri()`、`Quad()`、`Hex()` 要素タイプでサポートされています）。
  * `RefElemData_kwargs` は `RefElemData` の追加キーワード引数で、`quad_rule_vol` などがあります。詳細については、[StartUpDG.jl docs](https://jlchan.github.io/StartUpDG.jl/dev/)を参照してください。
