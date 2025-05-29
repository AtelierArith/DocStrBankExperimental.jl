```
SurfaceLiquidRateTarget(q)
```

Well target of specified liquid rate at surface conditions with value `q`. Typically used for a [`ProducerControl`](@ref) as you have full control over the mixture composition during injection.

Liquid rate, sometimes abbreviated LRAT, is made up of the phases that remain liquid at surface conditions. Typically, this will be water and oil if present in the model, but never different types of gas. If a producing becomes nearly or completely flooded by gas the well can go to very high or even infinite flows. It is therefore important to combine this control with a limit such as a bottom-hole-pressure constraint.
