```
ECI位置を変換してECEF位置を計算します
```

```julia
sat_position_ECI_2_ECEF(sat_state)

```

```
´sat_state´: 衛星状態、デコードされたデータ、コードおよびキャリアフェーズを組み合わせたもの


この関数は、ECI座標系におけるSVの位置を計算し、
この位置をECEF座標系に変換します。
実装はIS-GPS-200Kに従っています
```
