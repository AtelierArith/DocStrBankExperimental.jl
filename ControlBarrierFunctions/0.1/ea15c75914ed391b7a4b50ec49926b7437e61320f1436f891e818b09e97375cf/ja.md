```
ControlBarrierFunction
```

制御バリア関数 (CBF) は、そのゼロ超レベル集合として安全な集合を定義します。

# フィールド

  * `h::Function` : 安全な集合を定義する関数 `h(x) ≥ 0`
  * `α::Function` : CBF のための拡張クラス K 関数 `a(h(x))`
  * `∇h::Function` : CBF の勾配
  * `Lfh::Function` : ドリフトベクトル場 `f` に沿った CBF のリーデリバティブ
  * `Lgh::Function` : 制御方向 `g` に沿った CBF のリーデリバティブ
