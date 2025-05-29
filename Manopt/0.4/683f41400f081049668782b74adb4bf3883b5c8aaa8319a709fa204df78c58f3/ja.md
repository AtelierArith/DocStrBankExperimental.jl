```
LinearizedDCCost
```

関数 `(M,q) → ℝ` は [`ManifoldDifferenceOfConvexObjective`](@ref) の内部問題を表します。これは次の形式のコスト関数です。

$$
    F_{p_k,X_k}(p) = g(p) - ⟨X_k, \log_{p_k}p⟩
$$

点 `p_k` と接ベクトル `X_k` が `p_k` で（例えば外部反復）このファンクタ内に保存されます。

# フィールド

  * `g` 関数
  * `pk` マンフォールド上の点
  * `Xk` `pk` での接ベクトル

両方の中間値は `set_manopt_parameter!(::LinearizedDCCost, ::Val{:p}, p)` と `set_manopt_parameter!(::LinearizedDCCost, ::Val{:X}, X)` を使用して設定できます。

# コンストラクタ

```
LinearizedDCCost(g, p, X)
```
