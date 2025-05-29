`add!(H::HG{T}, v::T)` to add a vertex to `H`. **Example**: `add!(H,3)`.

`add!(H::HG{T}, e::Set{T})` to add a hyperedge. This also works if `e` is a one-dimensional array of `T`s. **Example**: `add!(H,[1,2,3])`.
