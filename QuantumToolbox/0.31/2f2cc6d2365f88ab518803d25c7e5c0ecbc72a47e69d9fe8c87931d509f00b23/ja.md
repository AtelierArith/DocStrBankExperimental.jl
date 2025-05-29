```
phase(N::Int, ϕ0::Real=0)
```

単一モードのペグ・バーネット位相演算子で、ヒルベルト空間のカットオフ $N$ と参照位相 $\phi_0$ を持ちます。

この演算子は次のように定義されます。

$$
\hat{\phi} = \sum_{m=0}^{N-1} \phi_m |\phi_m\rangle \langle\phi_m|,
$$

ここで

$$
\phi_m = \phi_0 + \frac{2m\pi}{N},
$$

および

$$
|\phi_m\rangle = \frac{1}{\sqrt{N}} \sum_{n=0}^{N-1} \exp(i n \phi_m) |n\rangle.
$$

# 参考文献

  * [Michael Martin Nieto, QUANTUM PHASE AND QUANTUM PHASE OPERATORS: Some Physics and Some History, arXiv:hep-th/9304036](https://arxiv.org/abs/hep-th/9304036), Equation (30-32).
