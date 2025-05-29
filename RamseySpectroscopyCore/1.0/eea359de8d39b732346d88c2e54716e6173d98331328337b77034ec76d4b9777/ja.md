```
PerturbEvol
```

量子物理演算子の構造体で、摂動場の存在下での量子二準位系の進化を記述します。

# フィールド

  * `operator`:   行列の形で演算子自体を表します。

# 引数

  * `δ` :   `デチューニング`、摂動場の振動周波数が遷移に対してどれだけオフレゾナンスであるかの尺度（Hz）。
  * `τ` :   Rabi/Ramseyパルスの`持続時間`（s）。
  * `Ω₀` :   摂動場の中で二つのエネルギーレベルの確率振幅が変動する`ラビ周波数`（Hz）。

# 戻り値

  * `PerturbEvol` :   複合型インスタンス。

# 参照

  * [`StateVector`](@ref)

# 参考文献

  * Wikipedia: https://en.wikipedia.org/wiki/Two-state*quantum*system
  * Wikipedia: https://en.wikipedia.org/wiki/Rabi_frequency
