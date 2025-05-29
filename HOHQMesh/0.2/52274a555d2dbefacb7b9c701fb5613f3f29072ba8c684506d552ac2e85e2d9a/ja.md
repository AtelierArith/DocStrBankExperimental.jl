```
addBackgroundGrid!(proj::Project, box::Array{Float64},  N::Array{Int} )
```

境界ボックス = [上, 左, 下, 右] と各方向の区間数を指定して背景グリッドブロックを追加します。モデルに外部境界が定義されていない場合に使用します。
