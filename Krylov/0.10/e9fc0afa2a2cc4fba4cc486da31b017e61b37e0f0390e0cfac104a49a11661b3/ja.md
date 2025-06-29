```
V, Ψ, T, U, Φᴴ, Tᴴ = nonhermitian_lanczos(A, B, C, k)
```

#### 入力引数

  * `A`: 次元 `n` の正方行列をモデル化する線形演算子;
  * `B`: サイズ `n × p` の行列;
  * `C`: サイズ `n × p` の行列;
  * `k`: ブロック非エルミート・ランチョス法の反復回数.

#### 出力引数

  * `V`: 密な `n × p(k+1)` 行列;
  * `Ψ`: `V₁Ψ = B` を満たす密な `p × p` 上三角行列;
  * `T`: 帯域幅 `p` のスパースな `p(k+1) × pk` ブロック三重対角行列;
  * `U`: 密な `n × p(k+1)` 行列;
  * `Φᴴ`: `U₁Φᴴ = C` を満たす密な `p × p` 上三角行列;
  * `Tᴴ`: 帯域幅 `p` のスパースな `p(k+1) × pk` ブロック三重対角行列.
