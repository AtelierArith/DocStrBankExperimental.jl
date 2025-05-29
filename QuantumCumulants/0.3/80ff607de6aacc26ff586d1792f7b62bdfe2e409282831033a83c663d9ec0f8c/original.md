```
subst_reds(de::AbstractMeanfieldEquations)
```

Function that substitutes possible redundant conjugate averages inside the given Equations with their corresponding average given as the conjugate of one of the left-hand-side (of the equations) averages.

# Optional Arguments

*`scaling`: A Bool defining the way how averages are added to the `missed` vector. If true only averages, whose     operators (without indices) are not already inside the `missed` vector will be added.
