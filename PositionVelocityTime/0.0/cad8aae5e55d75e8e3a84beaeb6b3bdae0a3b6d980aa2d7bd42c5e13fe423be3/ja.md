```
ECEF位置を変換してECI位置を計算します
```

```julia
sat_position_rotation(sat_state, dt)

```

```
´sat_state´: 衛星状態、デコードされたデータ、コードおよびキャリアフェーズを組み合わせたもの


この関数は、SVのECEF座標での位置を計算し、
この位置をECI座標に変換します。
実装はIS-GPS-200Kに従います。
```
