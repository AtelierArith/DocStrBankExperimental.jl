```
reduce(p::S, G::sideal{S}) where S <: SPolyUnion
```

多項式 $p$ を理想 $G$ を生成する多項式によって還元した結果を返します。理想 $G$ はグレブナー基底である必要はありません。PLURAL 環 (S <: spluralg, GAlgebra, WeylAlgebra) においては、還元は左側の還元のみであり、したがって二側理想へのメンバーシップをテストするためには使用できません。LETTERPLACE 環 (S <: slpalg, FreeAlgebra) においては、還元は完全な二側還元であり、ここでは二側理想のみが構築できるためです。
