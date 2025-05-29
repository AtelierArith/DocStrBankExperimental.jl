```
relative_eff(
    sample::AbstractArray{<:Real, 3};
    source::Union{AbstractString, Symbol} = "default",
    maxlag::Int = typemax(Int),
    kwargs..., 
)
```

MCMCチェーンの相対効率を計算します。すなわち、効果的サンプルサイズを名目サンプルサイズで割ったものです。

`lowercase(String(source))` が `"default"` または `"mcmc"` の場合、相対効果的サンプルサイズは `MCMCDiagnosticTools.ess` を使用して計算され、キーワード引数 `kind = :basic`、`maxlag = maxlag`、および残りのキーワード引数 `kwargs...` が使用されます。それ以外の場合は、各チェーンに対して1のベクトルが返されます。

# 引数

  * `sample::AbstractArray{<:Real, 3}`: 形状が `(parameters, draws, chains)` の対数尤度値の配列です。
