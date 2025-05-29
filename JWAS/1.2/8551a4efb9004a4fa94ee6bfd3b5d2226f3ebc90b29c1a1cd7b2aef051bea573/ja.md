```
set_random(mme::MME,randomStr::AbstractString,ped::Pedigree, G;df=4)
```

  * 系統の情報 **ped** を持つランダム多因子効果として変数を設定します。および分散 **G**。
  * **G** は、自由度 **df** に対して割り当てられた分散の事前の平均です。デフォルトは 4.0 です。**G** が提供されない場合、応答（表現型）から値が計算されます。

```julia
#単一特性 (例 1)
model_equation  = "y = intercept + age + animal"
model           = build_model(model_equation,R)
ped             = get_pedigree(pedfile)
G               = 1.6
set_random(model,"animal", ped, G)

#単一特性 (例 2)
model_equation  = "y = intercept + age + animal + animal*age"
model           = build_model(model_equation,R)
ped             = get_pedigree(pedfile)
G               = [1.6   0.2
                   0.2  1.0]
set_random(model,"animal animal*age", ped,G)

#多特性
model_equations = "BW = intercept + age + sex + animal
                   CW = intercept + age + sex + animal"
model           = build_model(model_equations,R);
ped             = get_pedigree(pedfile);
G               = [6.72   2.84
                   2.84  8.41]
set_random(model,"animal",ped,G)
```
