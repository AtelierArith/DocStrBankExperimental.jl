```
c2d(css::ContinuouStateSpace, h::Float64, method::Symbol)
```

連続時間状態空間モデルを離散時間状態空間モデルに変換します。

**入力**

  * `css`: 連続時間状態空間モデル
  * `h`: サンプリング時間。
  * `method`: 離散化方法

      * `:zoh`: ゼロ次保持法
      * `:foh`: 一次保持法
      * `:blh`: 帯域制限保持法
      * `:rk4`: 4次ルンゲクッタ法

**出力**

  * `DiscreteStateSpace`: 離散時間状態空間モデル

      * `Ad`: 離散時間状態空間行列 A
      * `Bd`: 離散時間状態空間行列 B
      * `Bdp`: 離散時間状態空間行列 Bp（`:foh` および `:rk4` 方法のみ）
