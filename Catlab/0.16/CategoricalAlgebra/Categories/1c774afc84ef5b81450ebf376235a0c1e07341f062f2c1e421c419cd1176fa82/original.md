Abstract base type for a functor between categories.

A functor has a domain and a codomain ([`dom`](@ref) and [`codom`](@ref)), which are categories, and object and morphism maps, which can be evaluated using [`ob_map`](@ref) and [`hom_map`](@ref). The functor object can also be called directly when the objects and morphisms have distinct Julia types. This is sometimes but not always the case (see [`Category`](@ref)), so when writing generic code one should prefer the `ob_map` and `hom_map` functions.
