```
set_random(mme::MME,randomStr::AbstractString,G;Vinv=0,names=[],df=4)
```

  * set variables as random effects, defaulting to i.i.d effects, with variances **G**.
  * **G** is the mean for the prior assigned for the variance with degree of freedom **df**, defaulting to 4.0. If **G** is not provided, a value is calculated from responses (phenotypes).
  * the random effects are assumed to be i.i.d by default and it can be defined with any (inverse of) covariance structure **Vinv** with its index (row names) provided by **names**.

```julia
#single-trait (i.i.d randome effects)
model_equation  = "y = intercept + litter + sex"
model           = build_model(model_equation,R)
G               = 0.6
set_random(model,"litter",G)

#multi-trait (i.i.d randome effects)
model_equations = "BW = intercept + litter + sex
                   CW = intercept + litter + sex"
model           = build_model(model_equations,R);
G               = [3.72  1.84
                   1.84  3.41]
set_random(model,"litter",G)

#single-trait (randome effects with specific covariance structures)
model_equation  = "y = intercept + litter + sex"
model           = build_model(model_equation,R)
V               = [1.0  0.5 0.25
                   0.5  1.0 0.5
                   0.25 0.5 1.0]
G               = 0.6
set_random(model,"litter",G,Vinv=inv(V),names=[a1;a2;a3])
```
