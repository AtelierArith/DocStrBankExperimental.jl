```
sYlm_values(R, ℓₘₐₓ, spin)
sYlm_values(θ, ϕ, ℓₘₐₓ, spin)
```

スピン加重球面調和関数 ${}_{s}Y_{\ell, m}(R)$ の値をすべての $\ell \leq \ell_\mathrm{max}$ に対して計算します。

入力および出力値の詳細については [`sYlm_values!`](@ref) を参照してください。

この関数は、`R` または `θ, ϕ` の単一の値に対して ${}_{s}Y_{\ell, m}$ を評価する必要がある場合にのみ適切です。なぜなら、大きな配列を割り当て、多くの計算を行うため、再利用できる可能性があるからです。`R` または `θ, ϕ` の多くの値に対して行列を評価する必要がある場合は、[`sYlm_prep`](@ref) を使用してストレージを事前に割り当て、その後結果を使って [`sYlm_values!`](@ref) を呼び出すべきです。 ```
