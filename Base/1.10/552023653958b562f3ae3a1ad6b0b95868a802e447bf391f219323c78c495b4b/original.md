```
==(x, y)
```

Generic equality operator. Falls back to [`===`](@ref). Should be implemented for all types with a notion of equality, based on the abstract value that an instance represents. For example, all numeric types are compared by numeric value, ignoring type. Strings are compared as sequences of characters, ignoring encoding. For collections, `==` is generally called recursively on all contents, though other properties (like the shape for arrays) may also be taken into account.

This operator follows IEEE semantics for floating-point numbers: `0.0 == -0.0` and `NaN != NaN`.

The result is of type `Bool`, except when one of the operands is [`missing`](@ref), in which case `missing` is returned ([three-valued logic](https://en.wikipedia.org/wiki/Three-valued_logic)). For collections, `missing` is returned if at least one of the operands contains a `missing` value and all non-missing values are equal. Use [`isequal`](@ref) or [`===`](@ref) to always get a `Bool` result.

# Implementation

New numeric types should implement this function for two arguments of the new type, and handle comparison to other types via promotion rules where possible.

[`isequal`](@ref) falls back to `==`, so new methods of `==` will be used by the [`Dict`](@ref) type to compare keys. If your type will be used as a dictionary key, it should therefore also implement [`hash`](@ref).

If some type defines `==`, [`isequal`](@ref), and [`isless`](@ref) then it should also implement [`<`](@ref) to ensure consistency of comparisons.
