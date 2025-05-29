```
project(M::EssentialManifold, p, X)
```

行列 `X` を接空間に射影します

$$
T_{p} \text{SO}(3)^2 = T_{\text{vp}}\text{SO}(3)^2 ⊕ T_{\text{hp}}\text{SO}(3)^2,
$$

まず、[`vert_proj`](@ref) を使用して垂直空間 $T_{\text{vp}}\text{SO}(3)^2$ への射影を計算します。次に、`X` を水平空間 $T_{\text{hp}}\text{SO}(3)^2$ への直交射影は次のように定義されます

$$
\Pi_h(X) = X - \frac{\text{vert\_proj}_p(X)}{2} \begin{bmatrix} R_1^T e_z \\ R_2^T e_z \end{bmatrix},
$$

ここで $R_i = R_0 R'_i, i=1,2,$ であり、$R'_i$ はカメラ $i$ のポーズの一部 $g_i = (R'_i,T'_i) ∈ \text{SE}(3)$ で、$R_0 ∈ \text{SO}(3)$ は $R_0(T'_2-T'_1) = e_z$ となるようにします。
