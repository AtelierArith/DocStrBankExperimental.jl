```
NumParams(tf::Float64,dt::Float64,scheme::String,st::Int,tol::Float64)
```

時間進行スキームに必要な数値パラメータ。

## フィールド

  * `tf`: この実行の終了時間
  * `dt`: 時間ステップサイズ
  * `scheme`: 異なる係数の暗黙的ルンゲ・クッタ法を適用します。選択肢は「Liska」（2次）、 「BH3」（3次）、 「BH5」（4次）、 「Euler」（1次）、 「RK2」（2次）、 「RK22」（2次）です。
  * `st`: このRKスキームの段階数
  * `tol`: 適応時間ステップのために時間進行で使用される許容誤差
