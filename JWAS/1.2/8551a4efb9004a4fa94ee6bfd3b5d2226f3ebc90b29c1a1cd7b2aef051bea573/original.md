```
set_random(mme::MME,randomStr::AbstractString,ped::Pedigree, G;df=4)
```

  * set variables as random polygenic effects with pedigree information **ped**. and variances **G**.
  * **G** is the mean for the prior assigned for the variance with degree of freedom **df**, defaulting to 4.0. If **G** is not provided, a value is calculated from responses (phenotypes).

```julia
#single-trait (example 1)
model_equation  = "y = intercept + age + animal"
model           = build_model(model_equation,R)
ped             = get_pedigree(pedfile)
G               = 1.6
set_random(model,"animal", ped, G)

#single-trait (example 2)
model_equation  = "y = intercept + age + animal + animal*age"
model           = build_model(model_equation,R)
ped             = get_pedigree(pedfile)
G               = [1.6   0.2
                   0.2  1.0]
set_random(model,"animal animal*age", ped,G)

#multi-trait
model_equations = "BW = intercept + age + sex + animal
                   CW = intercept + age + sex + animal"
model           = build_model(model_equations,R);
ped             = get_pedigree(pedfile);
G               = [6.72   2.84
                   2.84  8.41]
set_random(model,"animal",ped,G)
```
