```
function_space_operator(basis_functions, nodes, source;
                        derivative_order = 1, accuracy_order = 0,
                        opt_alg = Optim.LBFGS(), options = Optim.Options(g_tol = 1e-14, iterations = 10000),
                        verbose = false)
```

`basis_functions`という関数の iterable によって張られた関数空間における一次導関数演算子を表す演算子を構築します。この演算子は、`nodes`を用いて区間`[x_min, x_max]`上に構築され、`x_min`は`nodes`の最小値、`x_max`は最大値として取られます。`nodes`は内部でソートされることに注意してください。`accuracy_order`は演算子の精度の順序であり、オプションで渡すことができますが、演算子には影響を与えません。この演算子は、Optim.jlを用いて最適化問題を解くことで構築されます。最適化アルゴリズムと最適化問題のオプションは、キーワード引数`opt_alg`と`options`で指定できます。詳細は[Optim.jlのドキュメント](https://julianlsolvers.github.io/Optim.jl/stable/user/config/)を参照してください。

返される演算子は一般的なインターフェースに従います。現在は[`MatrixDerivativeOperator`](@ref)でラップされていますが、将来的には変更される可能性があります。この関数を使用するには、`Optim`パッケージをロードする必要があります。

また、[`GlaubitzNordströmÖffner2023`](@ref)も参照してください。

!!! compat "Julia 1.9"
    この関数は少なくともJulia 1.9が必要です。


!!! warning "Experimental implementation"
    これは実験的な機能であり、将来のリリースで変更される可能性があります。

