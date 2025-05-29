```
set_random(mme::MME,randomStr::AbstractString,G;Vinv=0,names=[],df=4)
```

  * 変数をランダム効果として設定し、デフォルトでi.i.d効果を使用し、分散は**G**です。
  * **G**は、自由度**df**で分散に割り当てられた事前の平均です。デフォルトは4.0です。**G**が提供されない場合、応答（表現型）から値が計算されます。
  * ランダム効果はデフォルトでi.i.dと仮定され、任意の（逆）共分散構造**Vinv**で定義でき、そのインデックス（行名）は**names**で提供されます。

```julia
#単一形質（i.i.dランダム効果）
model_equation  = "y = intercept + litter + sex"
model           = build_model(model_equation,R)
G               = 0.6
set_random(model,"litter",G)

#多重形質（i.i.dランダム効果）
model_equations = "BW = intercept + litter + sex
                   CW = intercept + litter + sex"
model           = build_model(model_equations,R);
G               = [3.72  1.84
                   1.84  3.41]
set_random(model,"litter",G)

#単一形質（特定の共分散構造を持つランダム効果）
model_equation  = "y = intercept + litter + sex"
model           = build_model(model_equation,R)
V               = [1.0  0.5 0.25
                   0.5  1.0 0.5
                   0.25 0.5 1.0]
G               = 0.6
set_random(model,"litter",G,Vinv=inv(V),names=[a1;a2;a3])
```
