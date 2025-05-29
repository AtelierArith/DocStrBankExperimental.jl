Create types for open attributed C-sets from an attributed C-set type.

The type parameters of the given acset type should *not* be instantiated with specific Julia types. This function returns a pair of types, one for objects, a subtype of [`StructuredCospanOb`](@ref), and one for morphisms, a subtype of [`StructuredMulticospan`](@ref). Both types will have the same type parameters for attribute types as the given acset type.

Mathematically speaking, this function sets up structured (multi)cospans with a functor $L: A → X$ between categories of acsets that creates "discrete acsets." Such a "discrete acset functor" is a functor that is left adjoint to a certain kind of forgetful functor between categories of acsets, namely one that is a pullback along an inclusion of schemas such that the image of inclusion has no outgoing arrows. For example, the schema inclusion ${V} ↪ {E ⇉ V}$ has this property but ${E} ↪ {E ⇉ V}$ does not.

See also: [`OpenCSetTypes`](@ref).
