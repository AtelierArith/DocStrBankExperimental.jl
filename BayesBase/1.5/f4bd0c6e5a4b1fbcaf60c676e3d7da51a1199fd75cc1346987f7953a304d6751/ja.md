```
samplefloattype(distribution)
```

分布の型または、サンプルが `Multivariate` または `Matrixvariate` の場合は基になる浮動小数点型を返します。デフォルトでは `deep_eltype(sampletype(distribution))` にフォールバックします。

関連情報: [`sampletype`](@ref), [`promote_sampletype`](@ref), [`promote_samplefloattype`](@ref)
