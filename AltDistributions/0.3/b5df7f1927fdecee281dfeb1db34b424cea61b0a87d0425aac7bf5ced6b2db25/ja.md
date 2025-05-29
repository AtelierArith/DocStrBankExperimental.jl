```julia
AltMvNormal(μ, Σ)

```

平均 `μ` と共分散行列 `Σ` を持つ多変量正規分布。`Σ` は抽象行列（例えば、因子分解）または `I` であることができます。`Σ` が数値誤差のために対称でない場合は、`LinearAlgebra.Symmetric` でラップしてください。

`LL'=Σ` を直接使用するには、`AltMvNormal(Val(:L), μ, L)` コンストラクタを使用してください。

また、標準偏差と相関行列のコレスキー因子から `L` を定式化するために [`StdCorrFactor`](@ref) を参照してください：

```julia
AltMvNormal(Val(:L), μ, StdCorrFactor(σ, S))
```
