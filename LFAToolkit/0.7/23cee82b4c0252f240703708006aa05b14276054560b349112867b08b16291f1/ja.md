```julia
kosloff_talezer_transformation(α)
```

逆正弦関数から導出されたKosloffおよびTal-Ezerの準同型写像を計算します。

# 引数:

  * `α::Float64`: arcsin(s)のテイラー級数展開の多項式次数。

# 戻り値:

  * 準同型写像

# 例:

```jldoctest
# kosloff_talezer_transformation 準同型写像
g, gprime = LFAToolkit.kosloff_talezer_transformation(0.95);

# 検証
truegonrange = [-1.0, -0.39494881426787537, 0.0, 0.39494881426787537, 1.0];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# 出力

```
