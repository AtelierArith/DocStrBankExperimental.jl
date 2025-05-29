Given a value for each variable, create a morphism X → X′ which applies the  substitution. We do this via pushout.

O –> X    where C has AttrVars for `merge` equivalence classes    ↓          and O has only AttrVars (sent to concrete values or eq classes    C          in the map to C.

`subs` and `merge` are dictionaries keyed by attrtype names

`subs` values are int-keyed dictionaries indicating binding, e.g.  `; subs = (Weight = Dict(1 => 3.20, 5 => 2.32), ...)`

`merge` values are vectors of vectors indicating equivalence classes, e.g. `; merge = (Weight = [[2,3], [4,6]], ...)`
