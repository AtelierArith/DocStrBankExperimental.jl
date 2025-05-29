```
cosets(G, H)
```

部分群 `H` $=H$ が `G` = $G$ のとき、$H$ の (左) コセット代表の集合 $\{g_i\}$ を $G$ の中で見つけます。次のように（例として Inui et al. のセクション 2.7 を参照）

$$
    G = \bigcup_i g_i H.
$$

恒に単位操作 $1$ は $\{g_i\}$ に含まれます。

## 例

```jldoctest cosets
julia> G = pointgroup("6mm");

julia> H = pointgroup("3");

julia> Q = cosets(G, H)
4-element Vector{SymOperation{3}}:
 1
 2₀₀₁
 m₁₁₀
 m₋₁₁₀
```

関連するコセットを生成するには、単に代表を `H` と合成します：

```jldoctest cosets
julia> [compose.(Ref(q), H) for q in Q]
4-element Vector{Vector{SymOperation{3}}}:
 [1, 3₀₀₁⁺, 3₀₀₁⁻]
 [2₀₀₁, 6₀₀₁⁻, 6₀₀₁⁺]
 [m₁₁₀, m₁₀₀, m₀₁₀]
 [m₋₁₁₀, m₁₂₀, m₂₁₀]
```
