```
calculate_samples(m::Int, delta::Float64, alph::Float64)::Int
```

テンソル化されたチェビシェフ多項式基底に関する誤差境界を満たすのに十分なサンプルを生成します。

# 引数

  * `m::Int`: 多項式空間の次元。
  * `delta::Float64`: 相対誤差境界。
  * `alph::Float64`: 確率、信頼レベル。

# 戻り値

  * 必要なサンプル数。

# 例

```julia
calculate_samples(10, 0.1, 0.05)
```
