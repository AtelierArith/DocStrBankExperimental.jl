```julia
    (1) distanceMat(metric::Metric, 𝐏::ℍVector;
    <⏩=true>)

    (2) distanceMat(type::Type{T}, metric::Metric, 𝐏::ℍVector;
    <⏩=true>) where T<:AbstractFloat
```

1d 配列 $𝐏$ に $k$ 個の正定値行列 ${P_1,...,P_k}$ があるとき、[ℍVector type](@ref) の要素からなる $k⋅k$ の実 `LowerTriangular` 行列を作成し、要素 $δ(P_i, P_j)\textrm{, for all }i>=j$ を含みます。

これは、指定された `metric` を使用して、距離 $δ$ を生成する *相互距離* を保持する下三角行列です。タイプは [Metric::Enumerated type](@ref) です。 [`distance`](@ref) を参照してください。

メモリ使用量を最適化するために、下三角部分のみが計算されます。

デフォルトでは、結果の行列は `Float32` 型です。この型は、メソッド (2) を使用して別の実 `type` に変更できます。

この行列の要素は [`distanceSqrMat`](@ref) の平方根です。

<optional keyword arguments>:

  * ⏩=true の場合、相互距離の計算はマルチスレッドで行われます。

!!! note "Nota Bene"
    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示された場合、自動的に無効になります。 [Threads](@ref) を参照してください。


**See**: [distance](@ref).

**Examples**

```julia
using PosDefManifold
# 4つのランダムな10x10 SPD行列のセットを生成
Pset=randP(10, 4) # または、ユニコードを使用して: 𝐏=randP(10, 4)
Δ=distanceMat(Fisher, Pset)

# Float64型の行列を返す
Δ64=distanceMat(Float64, Fisher, Pset)

# 相互距離の完全な行列を取得
fullΔ=Hermitian(Δ, :L)
```
