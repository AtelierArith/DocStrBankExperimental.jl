```
evolutionOperatorA(H_lambda, S, Sinv, t)
```

進化演算子を定義に従って配列として取得します。

$$
U(t) = S e^{-i H_\lambda t / \hbar} S^{-1},
$$

ここで、$\hbar = 1$、$H_{\lambda,ii} = \lambda_i$ は $H$ の固有値であり、したがって $H$ は非特異でなければなりません。そうでない場合、$H_{\lambda,ij} = 0, i \neq j$ となります。$S$ は $H$ の固有分解から得られます。例えば、

```julia
H_lambda, S = eigen(Hamiltonian.data)
Sinv = inv(S)
H_lambda = diagm(H_lambda)
```

引数は配列でなければなりません。
