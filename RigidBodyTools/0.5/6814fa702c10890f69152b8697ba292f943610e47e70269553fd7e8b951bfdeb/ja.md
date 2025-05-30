```
maxvelocity(b::Union{Body,BodyList},x::AbstractVector,m::RigidBodyMotion[,tmax=10,dt=0.05])
```

与えられた運動状態ベクトル `x` と、体 `b` に適用される運動 `m` を通じて検索し、最大速度の大きさ `(umax,i,t,bid)`、それが発生する体の点のグローバルインデックス、発生する時間、およびそれが発生する体を返します。
