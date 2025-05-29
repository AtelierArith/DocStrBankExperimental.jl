```
groebner_walk(
  I::MPolyIdeal, 
  target::MonomialOrdering = lex(base_ring(I)),
  start::MonomialOrdering = default_ordering(base_ring(I));
  perturbation_degree = ngens(base_ring(I)),
  algorithm::Symbol = :standard
)
```

モノミアル順序に関して縮小されたグレブナー基底を計算するために、グレブナーウォークを使用して変換します。

# 引数

  * `I::MPolyIdeal`: グレブナー基底を計算したいイデアル。
  * `target::MonomialOrdering=:lex`: グレブナー基底を計算したいモノミアル順序。
  * `start::MonomialOrdering=:degrevlex`: 変換を開始するモノミアル順序。
  * `perturbationDegree::Int=2`: 変形されたウォークのための摂動次数。
  * `algorithm::Symbol=:standard`: グレブナーウォークの戦略。以下の中から選択できます：

      * `standard`: 標準ウォーク [Cox.Little.OShea:2005](@cite),
      * `generic`: 一般的なウォーク [Fukuda.Jensen.ea:2007](@cite),
      * `perturbed`: 摂動ウォーク [Amrhein.Gloor.ea:1996](@cite)。

# 例

```jldoctest
julia> R,(x,y) = polynomial_ring(QQ, ["x","y"]);

julia> I = ideal([y^4+ x^3-x^2+x,x^4]);

julia> groebner_walk(I, lex(R))
グレブナー基底の要素
1 -> x + y^12 - y^8 + y^4 r
2 -> y^16
に関して順序
lex([x, y])

julia> groebner_walk(I, lex(R); algorithm=:perturbed)
グレブナー基底の要素
1 -> x + y^12 - y^8 + y^4
2 -> y^16
に関して順序
lex([x, y])

julia> set_verbosity_level(:groebner_walk, 1);
julia> groebner_walk(I, lex(R))
標準ウォークの結果
交差した円錐: 
ZZRingElem[1, 1]
ZZRingElem[4, 3]
ZZRingElem[4, 1]
ZZRingElem[12, 1]
交差した円錐の数: 4
グレブナー基底の要素
1 -> x + y^12 - y^8 + y^4
2 -> y^16
に関して順序
lex([x, y])

julia> groebner_walk(I, lex(R); algorithm=:perturbed)
摂動ウォークの結果
交差した円錐: 
[4, 3]
[4, 1]
[5, 1]
[12, 1]
[1, 0]
交差した円錐の数: 5
グレブナー基底の要素
1 -> y^16
2 -> x + y^12 - y^8 + y^4
に関して順序
matrix_ordering([x, y], [1 0; 0 1])
```
