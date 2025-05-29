```julia
ScrambleMethod <: RandomizationMethod
```

スクランブルメソッドは、少なくともスクランブルベース `b`、使用する「ビット」の数 `pad`（デフォルトは `pad=32`）およびシード `rng`（デフォルトは `rng = Random.GLOBAL_RNG`）が必要です。スクランブルメソッドの実装者は

  * `DigitalShift`.
  * `OwenScramble`: Owen (1995) で導入されたネストされた一様スクランブル。
  * `MatousekScramble`: Matousek (1998) で導入された線形行列スクランブル。
