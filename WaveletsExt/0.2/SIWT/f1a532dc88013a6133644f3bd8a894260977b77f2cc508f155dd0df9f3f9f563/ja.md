```
bestbasistree!(siwtObj)
```

SIWTオブジェクトの最良基底木を計算し、最良基底木の一部でないすべてのノードを破棄します。

# 引数

  * `siwtObj::ShiftInvariantWaveletTransformObject{N,T₁,T₂} where {N, T₁<:Integer, T₂<:AbstractFloat}`: SIWTオブジェクト。

# 例

```julia
using Wavelets, WaveletsExt

# セットアップ
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwtObj = siwpd(x, wt)

# 最良基底木
bestbasistree!(siwtObj)
```

**関連情報:** [`bestbasis_treeselection!`](@ref), [`isvalidtree`](@ref)
