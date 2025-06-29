```
orbit(...)
```

提供されたキーワード引数から軌道を構築します。提供された情報に基づいて、AbstractOrbitのサブクラスを自動的に選択します。これは便利な関数ですが、型が安定しておらず、パフォーマンスに敏感なコンテキストでは使用すべきではありません。代わりに、具体的なコンストラクタ `KepOrbit`、`VisualOrbit`、または `RadialVelocityOrbit` を直接呼び出してください。この関数は、作成された要素の種類をログに記録するため、正しいコンストラクタを選択しやすくなっています。

必須引数:

  * a: 長半径 [AU]
  * M: 重力パラメータ [M⊙]

オプション引数:

  * tp: 近日点通過の時刻、デフォルト=0
  * e: 離心率、デフォルト=0
  * ω: 近日点引数 [rad]、デフォルト=0
  * i: 傾斜 [rad]
  * Ω: 昇交点の経度 [rad]
  * plx: 視差 [mas]; 主星までの距離を定義します
