Function between finite sets.

The function can be defined implicitly by an arbitrary Julia function, in which case it is evaluated lazily, or explictly by a vector of integers. In the vector representation, the function (1↦1, 2↦3, 3↦2, 4↦3), for example, is represented by the vector [1,3,2,3].

FinFunctions can be constructed with or without an explicitly provided codomain. If a codomain is provided, by default the constructor checks it is valid.

This type is mildly generalized by [`FinDomFunction`](@ref).
