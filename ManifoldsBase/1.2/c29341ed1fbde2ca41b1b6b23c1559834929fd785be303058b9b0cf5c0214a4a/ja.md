```
Weingarten(M, p, X, V)
```

Weingarten写像 $\mathcal W_p\colon T_p\mathcal M × N_p\mathcal M \to T_p\mathcal M$ を計算します。ここで、$N_p\mathcal M$ は埋め込まれた部分多様体 $\mathcal M$ の接空間 $T_p\mathcal M$ の直交補空間であり、埋め込みを $\mathcal E$ で示します。

Weingarten写像は、基準点 $p$ に関して直交 [`project`](@ref)ion $\operatorname{proj}_{T_p\mathcal M}\colon T_p \mathcal E \to T_p\mathcal M$ の微分を制限することによって定義できます。すなわち、

$$
\mathcal P_X := D_p\operatorname{proj}_{T_p\mathcal M}(Y)[X],
\qquad Y \in T_p \mathcal E, X \in T_p\mathcal M,
$$

Weingarten写像は $\mathcal W_p(X,V) = \mathcal P_X(V)$ と書くことができます。

Weingarten写像は [Julius Weingarten](https://en.wikipedia.org/wiki/Julius_Weingarten) (1836–1910) にちなんで名付けられました。
