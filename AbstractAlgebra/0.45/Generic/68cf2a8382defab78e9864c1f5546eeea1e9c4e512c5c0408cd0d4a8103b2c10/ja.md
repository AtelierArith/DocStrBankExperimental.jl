```
character(lambda::Partition)
```

$$
\lambda
$$

の順列群の$\lambda$-th irreducible characterを返します。返されるcharacter関数は以下のシグネチャを持ちます：

> `chi(p::Perm[, check::Bool=true]) -> BigInt`


関数は（`p`が適切な群に属するかどうか）を確認する機能を、`chi(p, false)`と呼ぶことでオフにすることができます。$\chi$によって計算された値はルックアップテーブルにキャッシュされます。

計算はMurnaghan-Nakayamaの公式に従います：$\chi_\lambda(\sigma) = \sum_{\text{rimhook }\xi\subset \lambda}(-1)^{ll(\lambda\backslash\xi)} \chi_{\lambda \backslash\xi}(\tilde\sigma)$ ここで、$\lambda\backslash\xi$は$\xi$を除いた$\lambda$のスキュー図を示し、$ll$は脚の長さ（すなわち行数 - 1）を示し、$\tilde\sigma$は最長のサイクルを除去した$\sigma$から得られる順列です。

詳細については、S.Sternbergの*Group Theory and Physics*の第2.8章を参照してください。

# 例

```jldoctest
julia> G = SymmetricGroup(4)
4要素の全対称群

julia> chi = character(Partition([3,1])); # 正則表現のcharacter


julia> chi(one(G))
3

julia> chi(perm"(1,3)(2,4)")
-1
```
