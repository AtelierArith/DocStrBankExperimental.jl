```
SVのECEF位置を計算します
```

```julia
sat_position_ECEF(sat_state)

```

```
´sat_state´: 衛星状態、デコードされたデータ、コードおよびキャリアフェーズを組み合わせたもの


この関数は、SVのECEF座標での位置を計算します。
実装はIS-GPS-200Kの表20-IVに従っています。
```
