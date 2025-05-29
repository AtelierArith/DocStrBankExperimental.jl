```
LinearizedDCGrad
```

内問題の勾配を表すファンクタ `(M,X,p) → ℝ` [`ManifoldDifferenceOfConvexObjective`](@ref) の。この勾配関数は次の形をしています。

$$
    F_{p_k,X_k}(p) = g(p) - ⟨X_k, \log_{p_k}p⟩
$$

その勾配は $F=F_1(F_2(p))$ を用いて与えられ、ここで $F_1(X) = ⟨X_k,X⟩$ および $F_2(p) = \log_{p_k}p$ であり、連鎖律とその引数に関する対偶微分を用いて $D^*F_2(p)$ を計算します。

$$
    \operatorname{grad} F(q) = \operatorname{grad} f(q) - DF_2^*(q)[X]
$$

点 `pk` と接ベクトル `Xk` がこのファンクタ内に格納されている外部反復のためのものです。

# フィールド

  * `grad_g!!` $g$ の勾配（[`LinearizedDCCost`](@ref) も参照）
  * `pk` マンifold上の点
  * `Xk` `pk` における接ベクトル

両方の中間値は `set_manopt_parameter!(::LinearizedDCGrad, ::Val{:p}, p)` および `set_manopt_parameter!(::LinearizedDCGrad, ::Val{:X}, X)` を使用して設定できます。

# コンストラクタ

```
LinearizedDCGrad(grad_g, p, X; evaluation=AllocatingEvaluation())
```

ここで `grad_g` が [`AllocatingEvaluation`](@ref) または [`InplaceEvaluation`](@ref) であるかを指定しますが、この関数は *両方* のシグネチャを提供します。
