```
riemannian_Hessian(M, p, eG, eH, X)
riemannian_Hessian!(M, Y, p, eG, eH, X)
```

ユークリッドヘッセ行列 `eH=`$\operatorname{Hess} \tilde f(p) [X]$ は、関数 $f \colon \mathcal M \to \mathbb R$ の制限である $\tilde f$ のもので、さらに（ユークリッド）勾配 $\operatorname{grad} \tilde f(p)$ が与えられます。

リーマンヘッセ行列は次のように計算されます。

$$
\operatorname{Hess} f(p)[X]
= \operatorname{proj}_{T_p\mathcal M}\bigl(\operatorname{Hess} \tilde f(p)[X])
+ \mathcal W_p\Bigl( X, \operatorname{proj}_{N_p\mathcal M}\bigl( \operatorname{grad} \tilde f (p) \bigr) \Bigr),
$$

ここで $N_p\mathcal M$ は法線空間を示し、すなわち埋め込みにおける接空間の直交補空間であり、$\mathcal W_p$ は [`Weingarten`](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/functions/#ManifoldsBase.Weingarten-Tuple{AbstractManifold,%20Any,%20Any,%20Any}) マップを示します。詳細については [Boumal:2023](@cite) を参照してください。

この関数は、[MatlabパッケージManopt](https://manopt.org) の `ehess2rhess` にインスパイアされています。
