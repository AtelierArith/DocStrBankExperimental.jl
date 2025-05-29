```
cf(::LinearEBayesTarget, t)
```

$$
L(\cdot)
$$

の特性関数であり、`LinearEBayesTarget`として定義されます。次のように定義します：

$$
L(\cdot)
$$

は$L(G) = \int \psi(\mu)dG\mu$（可測関数$\psi$の場合）と書くことができ、これは$t$で評価された$\psi$のフーリエ変換を返します。すなわち、$\psi^*(t) = \int \exp(it x)\psi(x)dx$です。$\psi^*(t)$は、密度$g$を持つ分布$G$に対して（$g^*$は$g$のフーリエ変換）、次のように成り立ちます：

$$
L(G) = \frac{1}{2\pi}\int g^*(\mu)\psi^*(\mu) d\mu
$$
