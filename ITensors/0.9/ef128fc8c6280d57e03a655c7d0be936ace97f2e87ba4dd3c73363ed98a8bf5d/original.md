An `Index` represents a single tensor index with fixed dimension `dim`. Copies of an Index compare equal unless their `tags` are different.

An Index carries a `TagSet`, a set of tags which are small strings that specify properties of the `Index` to help distinguish it from other Indices. There is a special tag which is referred to as the integer tag or prime level which can be incremented or decremented with special priming functions.

Internally, an `Index` has a fixed `id` number, which is how the ITensor library knows two indices are copies of a single original `Index`. `Index` objects must have the same `id`, as well as the `tags` to compare equal.
