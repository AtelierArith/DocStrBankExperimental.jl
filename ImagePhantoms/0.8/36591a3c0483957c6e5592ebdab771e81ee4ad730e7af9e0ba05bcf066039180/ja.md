```
spectrum(oa::Array{<:Object2d})::Function
```

ユーザーが任意の空間周波数位置でサンプリングできる関数 `kspace(fx,fy)` を返し、2Dオブジェクトの `Array` のスペクトル（2Dフーリエ変換）を評価します。
