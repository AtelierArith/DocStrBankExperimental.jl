```
GlobalSection(Y)
```

`Y`のためのグローバルセクションを構築します。  

グローバルセクション $\lambda$ は、同次空間 $\mathcal{M}$ から対応するリー群 $G$ への写像であり、次の条件を満たします。

$$
\lambda(Y)E = Y,
$$

また、[`apply_section`](@ref) と [`global_rep`](@ref) も参照してください。

# 実装

カスタム配列（特に多様体）に対する `GlobalSection` の実装のためには、関数 [`global_section`](@ref) を一般化する必要があります。
