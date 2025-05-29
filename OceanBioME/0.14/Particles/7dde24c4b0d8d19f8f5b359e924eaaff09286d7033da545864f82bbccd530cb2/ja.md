```
BiogeochemicalParticles(number; 
                        grid,
                        biogeochemistry,
                        advection = LagrangianAdvection(),
                        timestepper = ForwardEuler,
                        field_interpolation = NearestPoint(),
                        scalefactors = ones(number))
```

`number` 個の粒子を `grid` 上に `biogeochemistry` で作成し、`advection` によって移動させます。デフォルトは `LagrangianAdvection` で（水と共に移動します）。バイオジオケミストリーは `timestepper` によってステップされ、トレーサーフィールドは `field_interpolation` によって補間されます。デフォルトでは、最も近い中心点を直接読み取り、同じ場所に取り込み/放出します。

粒子は `scalefactor` を持つこともでき、これによりトレーサー相互作用をスケーリングします（例えば、複数の粒子を表す粒子を模倣するため）。
