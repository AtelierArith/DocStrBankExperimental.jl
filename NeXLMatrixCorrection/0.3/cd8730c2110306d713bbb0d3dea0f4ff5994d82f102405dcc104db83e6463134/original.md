The `UnmeasuredElementRule` mechanism provides a method to implement rules for adding unmeasured elements to the fitting process.  Examples include element-by-stoichiometry or element-by-difference.

`UnmeasuredElementRule` implementations must include methods for:

```
NeXLUncertainties.compute(uer::<:UnmeasuredElementRule, inp::Dict{Element,<:AbstractFloat})::Dict{Element,AbstractFloat}
isunmeasured(uer::<:UnmeasuredElementRule, elm::Element)::Bool
```
