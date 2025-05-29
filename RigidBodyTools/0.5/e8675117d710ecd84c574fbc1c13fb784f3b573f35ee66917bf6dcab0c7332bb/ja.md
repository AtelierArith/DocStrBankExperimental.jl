```
motion_rhs!(dxdt::AbstractVector,x::AbstractVector,p::Tuple{RigidBodyMotion,BodyList},t::Real)
```

リンクされたシステム `ls` のボディ `bl` のために、現在の状態ベクトル `x` と現在の時間 `t` を使用して、右辺ベクトル `dxdt` (変更可能) を設定します。
