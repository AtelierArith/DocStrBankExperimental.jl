```
mk_threshold(τ::Vector{T}, κ::Vector{Int}, m::Int, q::Number)
```

複数のノックオフ閾値 `τ̂ > 0` を選択します。ここで、τ̂ = min{ t > 0 : (1/m + 1/m * {#j: κ[j] ≥ 1 and W[j] ≥ t}) / {#j: κ[j] == 0 and W[j] ≥ τ̂} ≤ q } です。

# 入力

  * `τ`: τ[i] は i 番目の特徴の重要度スコアを格納します。すなわち、値は T0 - median(T1,...,Tm) です。Gimenez と Zou では、中央値の代わりに最大関数が使用されていることに注意してください。
  * `κ`: κ[i] は m 個のノックオフの中で最も重要度スコアが大きいものを格納します。元の変数が最も大きなスコアを持つ場合、κ[i] == 0 です。
  * `m`: 生成される各変数のノックオフの数
  * `q`: 目標 FDR (0 と 1 の間)
  * `rej_bounds`: 考慮する上位 τ の値の数 (デフォルト = 10000)

# 参考文献:

  * He らによる「Identification of putative causal loci in wholegenome sequencing data via knockoff statistics」の補足の式 8 および 9。
  * Gimenez と Zou による「Improving the Stability of the Knockoff Procedure: Multiple Simultaneous Knockoffs and Entropy Maximization」のアルゴリズム 1。
