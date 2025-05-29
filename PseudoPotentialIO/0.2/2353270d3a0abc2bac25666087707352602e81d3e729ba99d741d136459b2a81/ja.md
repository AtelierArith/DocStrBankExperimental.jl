```julia
struct HghPsP{T} <: PseudoPotentialIO.AnalyticalPsP
```

解析的ハートウィグゼン-ゴーデッカー-フッター擬ポテンシャル。

[C. Hartwigsen, S. Goedecker, and J. Hutter. *Pys. Rev. B* **58**, 3641 (1998)](https://doi.org/10.1103/PhysRevB.58.3641)

  * `checksum::Vector{UInt8}`: SHA1 チェックサム
  * `Zatom::Union{Nothing, T} where T`: 原子電荷
  * `Zval::Any`: 価電子電荷
  * `lmax::Int64`: 最大角運動量
  * `rloc::Any`: 擬ポテンシャルの局所部分のための半径カットオフ
  * `cloc::Vector`: 擬ポテンシャルの局所部分の多項式係数
  * `rnl::OffsetArrays.OffsetArray{T, 1, Vector{T}} where T`: 非局所プロジェクタのための半径カットオフ `rnl[l]`
  * `D::OffsetArrays.OffsetArray{Matrix{T}, 1, Array{Matrix{T}, 1}} where T`: 非局所プロジェクタ結合係数 `D[l][n,m]`
