```
onephoton(b::WaveguideBasis{T,1},ξ::AbstractArray;norm=false) where {T}
```

  * `b`は単一の波導のみを含むため、波導のインデックスは必要ありません。
  * `ξ`はlength(ξ) == b.nstepsの`AbstractArray`である必要があります。
  * `norm::Bool=false`: trueの場合、結果の波束を正規化します。
