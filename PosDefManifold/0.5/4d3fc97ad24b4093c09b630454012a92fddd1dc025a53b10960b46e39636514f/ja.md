```
    randEigvals(n::Int;
    <
    df::Int=2,
    eigvalsSNR::Real=10e3 >)
```

**エイリアス**: `randλ`

$$
n
$$

-次元のランダムな実の正の固有値のベクトルを生成します。固有値は、関数 `randΛ`（[`randEigvalsMat`](@ref)）と同様に生成され、使用される構文です。

**関連情報**: `randU`（[`randUnitaryMat`](@ref)）、`randP`（[`randPosDefMat`](@ref)）。

**例**

```julia
using Plots, PosDefManifold
λ=sort(randλ(10), rev=true)
σ=sort(randλ(10, eigvalsSNR=10), rev=true)
plot(λ) # Plotsパッケージが必要です。プロットのバックエンドを確認してください。
plot!(σ) # Plotsパッケージが必要です。プロットのバックエンドを確認してください。
```
