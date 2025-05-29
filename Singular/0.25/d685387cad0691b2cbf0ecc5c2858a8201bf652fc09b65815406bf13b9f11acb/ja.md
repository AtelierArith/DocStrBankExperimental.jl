```
reduce(I::sideal{S}, G::sideal{S}) where S <: SPolyUnion
```

理想 $I$ の生成元を理想 $G$ によって還元した理想を返します。理想 $G$ はグレブナー基底である必要はありません。返される理想は、ゼロであっても $I$ と同じ数の生成元を持ちます。PLURAL 環 (S <: spluralg, GAlgebra, WeylAlgebra) においては、還元は左側の還元のみであり、したがって両側理想内の包含をテストするためには使用できません。LETTERPLACE 環 (S <: slpalg, FreeAlgebra) においては、還元は両側であり、ここでは両側理想のみが構築可能です。
