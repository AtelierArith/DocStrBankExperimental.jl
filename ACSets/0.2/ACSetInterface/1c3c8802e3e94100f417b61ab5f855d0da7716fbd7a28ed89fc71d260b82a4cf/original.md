Type of part IDs to use in an acset.

The choice of parts type does not alter the mathematical model but it does affect the performance tradeoffs of the acset data structure, the assumptions that can be made about the part IDs, and whether garbage collection ([`gc!`](@ref)) is relevant.

Type parameter `S` is the collection type (`Int`, `BitSet`, etc) and type parameter `T` is the element type (`Int`, `Symbol`, etc), mirroring the two type parameters of `FinSet` in Catlab.

The default choice of parts type is [`DenseParts`](@ref).
