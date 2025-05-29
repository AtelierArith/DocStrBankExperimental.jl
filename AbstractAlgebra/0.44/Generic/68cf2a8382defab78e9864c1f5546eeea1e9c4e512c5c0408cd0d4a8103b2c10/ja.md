```
character(lambda::Partition)
```

$$
\lambda
$$

-次の不可約文字を `sum(lambda)` 個の記号の置換群から返します。返される文字関数のシグネチャは次のとおりです。

> `chi(p::Perm[, check::Bool=true]) -> BigInt`


関数は（`p` が適切な群に属するかどうか）を確認することができ、`chi(p, false)` を呼び出すことでオフにできます。$\chi$ によって計算された値はルックアップテーブルにキャッシュされます。

計算はムルナハン-ナカヤマの公式に従います：$\chi_\lambda(\sigma) = \sum_{\text{rimhook }\xi\subset \lambda}(-1)^{ll(\lambda\backslash\xi)} \chi_{\lambda \backslash\xi}(\tilde\sigma)$ ここで、$\lambda\backslash\xi$ は $\xi$ を取り除いた $\lambda$ のスキュー図を示し、$ll$ は脚の長さ（すなわち行数 - 1）を示し、$\tilde\sigma$ は最長のサイクルを取り除いた $\sigma$ から得られる置換です。

詳細については、S.Sternberg の *Group Theory and Physics* の第2.8章を参照してください。

# 例

```jldoctest
julia> G = SymmetricGroup(4)
4要素の全対称群

julia> chi = character(Partition([3,1])); # 正則表現の文字


julia> chi(one(G))
3

julia> chi(perm"(1,3)(2,4)")
-1
```
