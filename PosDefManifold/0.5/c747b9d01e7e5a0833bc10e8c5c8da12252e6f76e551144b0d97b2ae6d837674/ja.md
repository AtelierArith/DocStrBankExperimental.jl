```julia
    (1) distanceSqrMat(metric::Metric, 𝐏::ℍVector;
    <⏩=true>)

    (2) distanceSqrMat(type::Type{T}, metric::Metric, 𝐏::ℍVector;
    <⏩=true>) where T<:AbstractFloat
```

**エイリアス**: `distance²Mat`

1d 配列 $𝐏$ の $k$ 個の正定値行列 ${P_1,...,P_k}$ の [ℍVector type](@ref) に対して、すべての $i>=j$ に対して要素 $δ^2(P_i, P_j)$ を含む $k⋅k$ の実数 `LowerTriangular` 行列を作成します。

これは、指定された `metric` を使用して、距離関数 $δ$ を生じるタイプ [Metric::Enumerated type](@ref) のすべての *二乗間距離* を保持する下三角行列です。 [`distanceSqr`](@ref) を参照してください。

メモリ使用量を最適化するために、下三角部分のみが計算されます。

デフォルトでは、結果の行列は `Float32` 型です。この型は、メソッド (2) を使用して別の実数 `type` に変更できます。

<オプションのキーワード引数>:

  * ⏩=true (デフォルト) の場合、間距離の計算はマルチスレッドで行われます。

!!! 注 "Nota Bene"     [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1) は、Julia が1つのスレッドのみを使用するように指示された場合、自動的に無効になります。 [Threads](@ref) を参照してください。

**参照**: [distance](@ref).

**関連項目**: [`laplacian`](@ref), [`laplacianEigenMaps`](@ref), [`spectralEmbedding`](@ref).

**例**

```julia
using PosDefManifold
# 8つのランダムな10x10 SPD行列のセットを生成
Pset=randP(10, 8) # または、ユニコードを使用して: 𝐏=randP(10, 8)
# 対数ユークリッド距離に従って二乗間距離行列を計算します。
# これはフィッシャー距離と比較してはるかに速く、一般的に
# 良い近似です。
Δ²=distanceSqrMat(logEuclidean, Pset)

# Float64 型の行列を返す
Δ²64=distanceSqrMat(Float64, logEuclidean, Pset)

# 間距離の完全な行列を取得
fullΔ²=Hermitian(Δ², :L)
```
