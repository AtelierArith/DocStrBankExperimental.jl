```julia
abstract type NumericPsP{T} <: PseudoPotentialIO.AbstractPsP
```

数値擬ポテンシャルを表す抽象型。

すべての量はハートリー原子単位でなければなりません。

  * 長さはボーア半径 (a₀) で
  * エネルギーはハートリー (Ha / Eₕ) で
  * 電荷は電子の電荷 (e = 1) で
  * 質量は電子の質量 (mₑ) で
  * 力学的作用は縮退プランク定数 (ħ = 1) で

角運動量でインデックス付けされたベクトルは、インデックスがゼロから始まる `OffsetVector` であるべきです。これにより、自然に0から始まる角運動量 `l` を計算とインデックス付けの両方に使用できます。

必要なフィールド：

```julia
# チェックサム
checksum::Vector{UInt8}
# 電子電荷の単位での原子全電荷
Zatom::Number
# 電子電荷の単位での擬原子価電荷
Zval::Number
# 最大角運動量
lmax::Integer
# ボーア単位での半径メッシュ
r::AbstractVector{Real}
# ボーア単位での半径メッシュ間隔
dr::Union{Real, AbstractVector{Real}}
# ハートリー単位での半径メッシュ上の局所ポテンシャル (r²の前因子なし)
Vloc::AbstractVector{Real}
## `D` と `β` の単位は `⟨ βˡₙ | Dˡₙₙ | βˡₙ ⟩` がハートリーを与えるようにするべきです
# 非局所プロジェクタ結合定数 D[l][n,n']
D::OffsetVector{AbstractMatrix{Real}}
# 半径メッシュ上の非局所プロジェクタ、メッシュの二乗で掛けられたもの: r²β[l][n]
β::OffsetVector{AbstractVector{AbstractVector{Real}}}

## "オプショナル" フィールド (存在する必要があるが、Union{Nothing} である可能性がある)
# 半径メッシュ上のモデルコア電荷密度 (非線形コア補正)、メッシュの二乗で掛けられたもの: r²ρcore
ρcore::Union{Nothing,AbstractVector{Real}}
# 半径メッシュ上の擬原子価電荷密度、メッシュの二乗で掛けられたもの: r²ρval
ρval::Union{Nothing,AbstractVector{Real}}
# 半径メッシュ上の擬原子軌道、メッシュの二乗で掛けられたもの: r²χ[l][n]
χ::Union{Nothing,OffsetVector{AbstractVector{AbstractVector{Real}}}}
```
