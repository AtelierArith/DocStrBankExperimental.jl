```julia
sausage_transformation(d)
```

Gauss楕円体の準同型写像を、arcsin(s)の切断テイラー展開を使用して計算します。HaleとTrefethen（2008）の図4.1を参照してください。

# 引数:

  * `d::Int`: arcsin(s)の切断テイラー級数展開の多項式次数。

# 戻り値:

  * 準同型写像

# 例:

```jldoctest
# sausage_transformation 準同型写像
g, gprime = LFAToolkit.sausage_transformation(9);

# 検証
truegonrange = [
    -0.9999999999999999,
    -0.39765215163451934,
    0.0,
    0.39765215163451934,
    0.9999999999999999,
];
@assert g.(LinRange(-1, 1, 5)) ≈ truegonrange

# 出力

```
