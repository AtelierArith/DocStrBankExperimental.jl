```
generate_expect_data(domain::AbstractInfiniteDomain, 
                     prefs::Union{GeneralVariableRef, Vector{GeneralVariableRef}}, 
                     num_supports::Int; 
                     [kwargs...])::AbstractMeasureData
```

Generate a concrete instance of `AbstractMeasureData` in accordance with the  `domain` and infinite parameter(s) `prefs` given for computing the expectation.  This is intended as an internal method, but should be extended for user defined  infinite domain types.
