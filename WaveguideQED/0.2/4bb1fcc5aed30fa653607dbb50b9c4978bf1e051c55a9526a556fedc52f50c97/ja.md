```
onephoton(b::WaveguideBasis{T,Nw},i,ξvec;norm=false) where {T,Nw}
```

  * `b`は`Nw`の波導を含むため、必要な波導のインデックス。
  * `i`はonephoton波束が生成される波導のインデックス。
  * `ξ`は`AbstractArray`であり、length(ξ) == b.nstepsであるべき。
  * `norm::Bool=false`: trueの場合、結果の波束を正規化します。
