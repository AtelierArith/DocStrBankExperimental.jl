A domain that represents the full space.

The element type `T` in `FullSpace{T}` should only be seen as an indication of the expected types of the elements in the context where the domain is intended to be used. Due to the default, loose interpretation of `T`, any `FullSpace{T}` actually contains any `x` regardless of the type of `x`. For a strict domain of all elements of type `T`, or elements convertible exactly to `T`, use `TypeDomain{T}`.
