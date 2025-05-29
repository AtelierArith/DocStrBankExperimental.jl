```
WCUSUM <: AbstractStatistic
```

加重累積和統計量。

# 引数

  * `k::Float64`: WCUSUM統計量を計算するために使用されるCUSUMの許容定数。デフォルトは1.0です。
  * `λ::Float64`: 故障シグネチャの推定値を更新するための平滑化定数。0と1の間の値でなければなりません。デフォルトは0.2です。
  * `value::Float64`: 加重累積和統計量の初期値。デフォルトは0.0です。
  * `Q::Float64`: 加重累積和の残差値。デフォルトは0.0です。
  * `upw::Bool`: 平均の増加を監視するか（`true`）、減少を監視するか（`false`）。デフォルトは`true`です。

# 参考文献

Shu, L., Jiang, W., & Tsui, K.-L. (2008). A Weighted CUSUM Chart for Detecting Patterned Mean Shifts. Journal of Quality Technology, 40(2), 194-213. https://doi.org/10.1080/00224065.2008.11917725

# 例

```julia
stat = WCUSUM()
get_design(stat)            # returns [1.0, 0.2]
update_statistic(stat, 3.0) # returns 1.2
stat.Q                      # returns 0.6
```
