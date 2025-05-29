```
mag = bodemag!(ws::BodemagWorkspace, sys::LTISystem, w::AbstractVector)
```

インスタンスの[`BodemagWorkspace`](@ref)でインプレースで動作するボードの大きさを計算します。返される大きさの配列は`ws.mag`とエイリアスされています。出力配列`mag`は∈ 𝐑(ny, nu, nω)です。
