```
N, E = latlon2yx(φ₀, λ₀, φ, λ)
```

ガウス・クリューガー投影における地理座標と平面直交座標の間の座標変換。この関数は以下の文書に基づいています:         https://www.gsi.go.jp/common/000061216.pdf         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/xy2bl/xy2bl.htm         https://vldb.gsi.go.jp/sokuchi/surveycalc/surveycalc/algorithm/bl2xy/bl2xy.htm

### 入力引数

  * φ₀, λ₀ : 原点の緯度と中央子午線
  * φ , λ  : 地理的緯度と経度

### 戻り値

  * N, E   : 平面直交座標の北方向と東方向の座標

### 例

```julia-repl
julia> # ANSWER: y = 11543.6883, x = 22916.2436

julia> latlon2yx(36.0, 139.0+5.0/6.0, 36.103774791666666, 140.08785504166664)
(11543.688321484718, 22916.24355431881)
```
