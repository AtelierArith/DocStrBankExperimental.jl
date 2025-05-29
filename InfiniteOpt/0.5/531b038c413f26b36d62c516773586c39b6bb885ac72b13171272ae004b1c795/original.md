```
internal_semi_infinite_variable(vref::SemiInfiniteVariableRef,
                                key::Val{:my_ext_key})::SemiInfiniteVariable
```

Return the semi-infinite variable object of `vref` assuming it is an internal variable made during measure expansion within an optimizer model. This will apply to optimizer model extensions that utilize `add_measure_variable` in combination with `expand_measure`.
