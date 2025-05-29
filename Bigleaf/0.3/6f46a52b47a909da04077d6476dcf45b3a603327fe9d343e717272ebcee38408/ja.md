```
Reynolds_Number(Tair,pressure,ustar,z0m; constants)
```

粗さレイノルズ数を計算します。

# 引数

  * `Tair`      : 空気温度 (℃)
  * `pressure`  : 大気圧 (kPa)
  * `ustar`     : 摩擦速度 (m s-1)
  * `z0m`       : 粗さ長 (m)

オプション

  * `constants=`[`BigleafConstants`](@ref)`()`

# 詳細

粗さレイノルズ数は、Massman 1999aに従って計算されます:      $Re = z0m * ustar / v$、ここで `v` は運動粘度 (m2 s-1) です。

# 値

粗さレイノルズ数 (-)

# 参考文献

Massman, W_J., 1999a: 植生表面のための kB H- 1 のモデル研究 'localized near-field' ラグランジュ理論を使用。水文学ジャーナル 223, 27-43。

```jldoctest; output = false
Tair,pressure,ustar,z0m = 25.0,100.0,0.5,0.5
R = Reynolds_Number(Tair,pressure,ustar,z0m)                             
≈(R, 15870, rtol=1e-3) 
# output
true
```
