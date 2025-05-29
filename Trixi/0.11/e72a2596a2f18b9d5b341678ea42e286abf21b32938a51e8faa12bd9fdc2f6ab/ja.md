```
DGMulti(approximation_type::AbstractDerivativeOperator;
        element_type::AbstractElemShape,
        surface_flux=flux_central,
        surface_integral=SurfaceIntegralWeakForm(surface_flux),
        volume_integral=VolumeIntegralWeakForm(),
        kwargs...)
```

与えられた `element_type` に対して、1D SBP 微分演算子を基にしたテンソル積構造を使用して、部分和（SBP）離散化を作成します。

詳細については、[StartUpDG.jl](https://jlchan.github.io/StartUpDG.jl/dev/) と [SummationByPartsOperators.jl](https://ranocha.de/SummationByPartsOperators.jl/stable/) のドキュメントを参照してください。
