```
siwpd(x, wt[, L, d])
```

Cohen, Raz & Malah によって元々開発されたシフト不変ウェーブレットパケット分解を、ベクトル `x` に対して離散ウェーブレットフィルタ `wt` を使用して `L` レベルと深さ `d` で計算します。

# 引数

  * `x::AbstractVector{T} where T<:AbstractFloat`: 1D信号。
  * `wt::OrthoFilter`: ウェーブレットフィルタ。
  * `L::S where S<:Integer`: (デフォルト: `maxtransformlevels(x)`) 変換レベルの数。
  * `d::S where S<:Integer`: (デフォルト: `L`) 各ノードのシフト変換の深さ。`d` の値は `L` 以下でなければなりません。

# 戻り値

  * ノードとツリーの詳細を含む `ShiftInvariantWaveletTransformObject`。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwpd(x, wt)        
siwpd(x, wt, 4)     # レベル4の分解、各分解は4レベルのシフト分解を持つ。
siwpd(x, wt, 4, 2)  # レベル4の分解、各分解は2レベルのシフト分解を持つ。
```

**参照:** [`isiwpd`](@ref), [`siwpd_subtree!`](@ref)
