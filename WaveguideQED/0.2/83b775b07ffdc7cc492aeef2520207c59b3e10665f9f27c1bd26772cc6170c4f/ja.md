```
onephoton(b::WaveguideBasis{T,1},ξ::Function,args...,norm=false) where {T}
```

  * `b`が単一の波導のみを含むため、波導のインデックスは必要ありません。
  * `ξ`はξ.(times,args...)としてブロードキャスト可能である必要があります。ここで、`times  = 0:b.dt:(b.nsteps-1)*b.dt`（波導基底を定義するために使用される時間）。
  * `args...`: `ξ`が関数である場合に渡される追加の引数。
  * `norm::Bool=false`: trueの場合、結果の波束を正規化します。
