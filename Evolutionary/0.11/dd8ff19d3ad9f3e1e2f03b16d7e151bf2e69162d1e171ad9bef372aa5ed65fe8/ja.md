```
uniformranking(μ)
```

(μ, λ)-一様ランキング選択関数を返します。最良の個体パラメータ `μ` については、[Selection Interface](@ref) を参照してください。

一様ランキングでは、最良の $\mu$ 個体に選択確率 $1/\mu$ が割り当てられ、残りは破棄されます [^2]。
