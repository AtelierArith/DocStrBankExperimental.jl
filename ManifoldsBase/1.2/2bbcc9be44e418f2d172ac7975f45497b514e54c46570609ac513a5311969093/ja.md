```
Y = Weingarten(TpM::TangentSpace, X, V, A)
Weingarten!(TpM::TangentSpace, Y, p, X, V)
```

点 `X` における Weingarten 写像 $\mathcal W_X$ を、接ベクトル $V \in T_p\mathcal M$ と法線ベクトル $A \in N_p\mathcal M$ に関して [`TangentSpace`](@ref) `TpM` で計算します。

これは平坦な空間であるため、結果は常にゼロ接ベクトルになります。
