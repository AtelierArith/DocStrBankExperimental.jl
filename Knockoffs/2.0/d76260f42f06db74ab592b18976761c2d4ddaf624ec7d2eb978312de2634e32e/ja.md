```
form_emission_prob_matrix(a, θ, xi::AbstractVector)
```

# 入力

  * `a`: fastPHASEから推定された値を持つ`p × K`行列（すなわち、彼らはこれをαパラメータと呼んでいる）
  * `θ`: fastPHASEから推定された値を持つ`p × K`行列
  * `xi`: サンプル`i`の遺伝子型を持つ長さ`p`のベクトル（エントリは0、1または2）
