```
bspline!(p::Path{T}, nextpoints, α_end, sty::Style=contstyle1(p), endpoints_speed=2500μm)
```

現在の `p` のエンドポイントから `nextpoints` を通るBSpline補間を追加します。

補間は `nextpoints[end]` に到達し、正のx軸との角度は `α_end` になります。`endpoints_speed` は補間がエンドポイントを出入りする「速さ」です。速度が高いほど、開始角度と終了角度はおおよそ α1(p) と α_end の間でより長い距離にわたります。
