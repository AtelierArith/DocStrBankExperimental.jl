```
onephoton(b::WaveguideBasis{T,Nw},i::Int,ξ::Function,args...; norm=false) where {T,Nw}
```

  * `b`が`Nw`の波導を含むため、必要な波導のインデックス。
  * `i`は、onephoton波束が生成される波導のインデックス。
  * `ξ`は、ξ.(times,args...)としてブロードキャスト可能である必要があります。ここで、`times  = 0:b.dt:(b.nsteps-1)*b.dt`（波導基底を定義するために使用される時間）。
  * `args...`: `ξ`が関数である場合に渡される追加の引数。
  * `norm::Bool=false`: trueの場合、結果の波束を正規化します。
