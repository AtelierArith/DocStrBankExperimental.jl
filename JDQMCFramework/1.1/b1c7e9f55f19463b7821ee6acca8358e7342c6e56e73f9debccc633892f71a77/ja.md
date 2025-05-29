```
exp!(
    exppαH::AbstractMatrix{T},
    expmαH::AbstractMatrix{T},
    H::AbstractMatrix{T}, α::E;
    # キーワード引数
    workspace::HermitianEigenWs{T,Matrix{T},R} = HermitianEigenWs(H),
    tol::R = 1e-6
) where {T<:Number, E<:Number, R<:AbstractFloat}
```

与えられたエルミート行列 `H` に対して、行列指数関数 $e^{+\alpha H}$ と $e^{-\alpha H}$ を計算し、それぞれ `exppαH` と `expmαH` に書き込みます。このメソッドによって `H` は左側で修正されることに注意してください。`workspace` フィールドは [`HermitianEigenWs`](https://dynarejulia.github.io/FastLapackInterface.jl/dev/workspaces/#FastLapackInterface.HermitianEigenWs) 型であり、[`FastLapackInterface.jl`](https://github.com/DynareJulia/FastLapackInterface.jl) パッケージからエクスポートされており、動的メモリ割り当てを避けるために使用されます。
