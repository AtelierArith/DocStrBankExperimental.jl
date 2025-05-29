```
ControlBarrierFunction
```

Control barrier function (CBF) defining a safe set as its zero superlevel set.

# Fields

  * `h::Function` : function defining the safe set `h(x) ≥ 0`
  * `α::Function` : extended class K function `a(h(x))` for CBF
  * `∇h::Function` : gradient of CBF
  * `Lfh::Function` : Lie derivative of CBF along drift vector field `f`
  * `Lgh::Function` : Lie derivative of CBF along control directions `g`
