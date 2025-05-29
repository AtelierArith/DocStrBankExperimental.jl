```
isiwpd(siwtObj)
```

コーエン、ラズ、マラによって最初に開発された逆シフト不変ウェーブレットパケット分解を計算します。

# 引数

  * `siwtObj::ShiftInvariantWaveletTransformObject{N,T₁,T₂} where {N,T₁<:Integer,T₂<:AbstractFloat`: SIWTオブジェクト。

# 戻り値

  * `Vector{T₂}`: 再構成された信号。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwtObj = siwpd(x, wt)

# ISIWPD
isiwpd(siwtObj)
```

**参照:** [`siwpd`](@ref), [`isiwpd_subtree!`](@ref)
