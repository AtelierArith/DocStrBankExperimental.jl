```
spectrum(oa::Array{<:Object3d})::Function
```

ユーザーが任意の空間周波数位置でサンプリングできる関数 `kspace(fx,fy,fz)` を返します。これは、3Dオブジェクトの `Array` のスペクトル（3Dフーリエ変換）を評価するためのものです。
