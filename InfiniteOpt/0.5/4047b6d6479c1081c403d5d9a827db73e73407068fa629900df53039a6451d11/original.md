```
make_generative_supports(info::AbstractGenerativeInfo,
                         pref::IndependentParameterRef,
                         existing_supps::Vector{Float64}
                         )::Vector{Float64}
```

Generate the generative supports for `pref` in accordance with `info` and the  `existing_supps` that `pref` has. The returned supports should not include  `existing_supps`. This is intended as internal method to enable  [`add_generative_supports`](@ref) and should be extended for any user defined  `info` types that are created to enable new measure and/or derivative evaluation  techniques that require the creation of generative supports.
