```
tps_solve(x,y,λ,compute_affine=true)
```

tps変換の解を見つける（いくつかの操作に必要ですが、追加の時間がかかります。）

# 引数

```
`x`: 制御点
`y`: 変形（歪んだ）制御点
`λ`: 剛性係数
`compute_affine`: `true`の場合、アフィン成分を計算します
```

`ThinPlateSpline`構造体を返し、これは`tps_deform`に引数として供給できます。

# 参照

```
`ThinPlateSpline`
```
