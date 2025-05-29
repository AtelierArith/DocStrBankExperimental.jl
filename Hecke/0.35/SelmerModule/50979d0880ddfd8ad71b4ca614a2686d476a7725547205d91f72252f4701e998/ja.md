```
pselmer_group_fac_elem(p::Int, S::Vector{<:AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}; check::Bool = true, algo::Symbol = :raw)
```

$$
K
$$

を$S$の素イデアルの数体とします。すると、$p$-Selmer群は、すべての評価が$S$の外で$p$で割り切れるような要素の$p$-乗の剰余類としての$K^*$の部分群です。

これは、$S$の外で非分岐な最大の根$p$-拡大をパラメータ化します。

このバージョンでは、要素は因子分解された形で返されます。`algo`パラメータは`:raw`または`:compRep`に設定できます。後者の場合、代表元は$p$-乗の剰余類に還元されます。ただし、主理想の支持はランダムである可能性があります。

`check`は、前像写像が要素が実際にコドメインに含まれているかをテストするかどうかを制御します。

`pselmer_group`も参照してください。

# 例

```jldoctest
julia> k, a = wildanger_field(3, 13);

julia> zk = maximal_order(k);

julia> S = collect(keys(factor(6*zk)));

julia> Sel, map = pselmer_group_fac_elem(2, S);

julia> g = evaluate(map(Sel[3]));

julia> K, _ = radical_extension(2, g);

julia> ZK = maximal_order(K);

julia> issubset(Set(keys(factor(discriminant(ZK)))) , S)
true

```
