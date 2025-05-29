```
AMCUSUM(λ, p; minshift = 0.1, shift = 0.0, Et = zeros(p), t = 0, stat = MCUSUM(k=0.1, p=p))
```

適応型多変量累積和（MCUSUM）統計量。

### 引数

  * `λ::Float64`: 平滑定数で、0.0 <= λ <= 1.0 である必要があります。
  * `p::Int`: 監視する品質変数の数。
  * `minshift::Float64`: 検出される最小シフト値。デフォルトは 0.1 です。
  * `shift::Float64`: 現在のシフト値。デフォルトは 0.0 です。
  * `Et::Vector{Float64}`: ゼロ平均からの平滑化された偏差のベクトル Et。`zeros(p)` と正確に等しくなければなりません。
  * `t::Int`: 現在の時間の値。デフォルトは 0 です。
  * `stat::C`: 基本的な古典的 MCUSUM 統計量。デフォルトは MCUSUM(k=0.1, p=p) です。

### 参考文献

Dai, Y., Luo, Y., Li, Z., & Wang, Z. (2011). A new adaptive CUSUM control chart for detecting the multivariate process mean. Quality and Reliability Engineering International, 27(7), 877-884. https://doi.org/10.1002/qre.1177
