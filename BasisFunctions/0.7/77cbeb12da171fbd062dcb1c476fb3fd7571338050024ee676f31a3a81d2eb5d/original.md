Create a tensor product of the supplied arguments.

The function `tensorproduct` applies some simplifications and does not necessarily return a Product type.

A `tensorproduct(a)` with just a single element returns `a`.

For integer `n`, `tensorproduct(a, n)` becomes `tensorproduct(a, a, ..., a)`. A type-safe variant is `tensorproduct(a, Val{N})`.
