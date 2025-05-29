```
Prox
```

準最適化アルゴリズムで使用されるプロキシポリシーを指定するための最適化属性。オプションは次のとおりです：

  * [`NoProx`](@ref): 制約なし。
  * [`Polyhedron`](@ref): 多面体空間へのQP射影 ?PolyhedronProjection のパラメータ説明。（デフォルト）
  * [`AndersonAcceleration`](@ref): 内部プロキシステップのアンダーソン加速 ?AndersonAcceleratedProximal のパラメータ説明。
  * [`Nesterov`](@ref): 内部プロキシステップのネステロフ加速 ?NesterovProximal のパラメータ説明。
  * [`DryFriction`](@ref): 内部プロキシステップのドライフリクション加速 ?DryFrictionProximal のパラメータ説明。
