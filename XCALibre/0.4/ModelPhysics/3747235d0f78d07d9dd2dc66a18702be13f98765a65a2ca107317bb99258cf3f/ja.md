```
WeaklyCompressible <: AbstractCompressible
```

弱圧縮流体モデルは、定数パラメータを持つ弱圧縮流れのための流体フィールドパラメータを含んでいます - 定常粘度を持つ理想気体。

### フィールド

  * 'nu'   – 流体の運動粘度。
  * 'cp'   – 流体の比熱容量。
  * `gamma` – 比熱の比。
  * `Pr`   – 流体のプラントル数。

### 例

  * `Fluid{WeaklyCompressible}(; nu=1E-5, cp=1005.0, gamma=1.4, Pr=0.7)` - デフォルト値を持つコンストラクタ。
