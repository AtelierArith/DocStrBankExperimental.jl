```
get_rho(psi::AbstractVector{T}; S::Real=1/2, LA::Int=0)
```

サブシステムサイズ `LA` が指定されていない場合はデフォルトで L÷2 となる縮退密度行列 ρ を返します。ここでは、非制限ヒルベルト空間のケースを考えています。すなわち、`psi` の次元は base^L です。

制限ヒルベルト空間のケース、例えば PXP モデルのスピンシステムの Mz セクターでは、現在の単純な方法はかなり遅くなる可能性があります。この場合は、代替方法を使用してください。

# 例

```julia-reply
julia> rho = get_rho(psi; S=1)
julia> rho = get_rho(psi; LA=4)
julia> rho = get_rho(psi; S=1/2, LA=4)
```
