```
sd(J::T, ω) where T <: AbstractSD
```

与えられた周波数 `ω` における `J` で表されるスペクトル密度を評価します。すなわち、`J(ω)`。

# 引数

  * `J::T`: スペクトル密度。
  * `ω`: スペクトル密度が評価される周波数。

# 戻り値

  * 周波数 `ω` におけるスペクトル密度 `J`。
