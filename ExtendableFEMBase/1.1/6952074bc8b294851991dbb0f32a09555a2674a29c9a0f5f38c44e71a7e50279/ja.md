```julia
mutable struct QPInfos{Ti, Tv, Ttime, Tx, Txref, TvG, TiG, PT}
```

現在の四分点に関する情報を共有するオブジェクト（現在の AssemblyType に対するアイテム番号、合理的な場合のセル番号、現在の AssemblyType に対する領域番号、アイテムの体積、合理的な場合の法線、現在の時間、現在の世界座標、現在の参照座標、パラメータのセット）
