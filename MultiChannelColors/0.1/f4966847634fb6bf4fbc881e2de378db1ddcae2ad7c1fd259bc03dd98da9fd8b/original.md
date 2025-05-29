```
ctemplate = ColorMixture((rgb₁, rgb₂))        # create an all-zeros ColorMixture with N0f8 channel intensities
ctemplate = ColorMixture{T}((rgb₁, rgb₂))     # same, but specify the element type
c = ctemplate((i₁, i₂))                       # Construct non-zero ColorMixture of the same type as `ctemplate`
```

Create a ColorMixture "template" `ctemplate` from which other non-zero colors `c` may be created.

`ctemplate((i...,))` is a constructor form that is performance-favorable, if the type of `ctemplate` is known. In conjunction with a [function barrier](https://docs.julialang.org/en/v1/manual/performance-tips/#kernel-functions), this form can be used to circumvent performance problems due to poor inferrability.
