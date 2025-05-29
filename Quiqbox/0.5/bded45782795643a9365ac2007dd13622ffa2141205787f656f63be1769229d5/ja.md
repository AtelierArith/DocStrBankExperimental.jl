```
genCanOrbitals(fVars::HFfinalVars{T, D, <:Any, NN}; 
               roundAtol::Real=getAtolVal(T)) where {T, D, NN} -> 
NTuple{2, Vector{CanOrbital{T, D, NN}}}
```

ハートリー–フォック近似 `fVars` の結果から占有および非占有の標準軌道を生成します。構築された [`CanOrbital`](@ref) に保存されている各パラメータは、`roundAtol` の最も近い倍数に丸められます。`roundAtol` が `NaN` に設定されている場合、丸めは行われません。
