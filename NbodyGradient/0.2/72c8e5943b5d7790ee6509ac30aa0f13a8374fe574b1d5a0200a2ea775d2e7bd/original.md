```
ElementsIC(t0,H,elems)
```

Collects `Elements` and produces an `ElementsIC` struct.

# Arguments

  * `t0::T` : Initial time [Days].
  * `H` : Hierarchy specification.
  * `elems` : The orbital elements and masses of the system.

---

There are a number of way to specify the initial conditions. Below we've described the arguments `ElementsIC` takes. Any combination of `H` and `elems` may be used. For a concrete example see [Tutorials](@ref).

# Elements

  * `elems...` : A sequence of `Elements{T}`. Elements should be passed in the order they appear in the hierarchy (left to right).
  * `elems::Vector{Elements}` : A vector of `Elements`. As above, Elements should be in order.
  * `elems::Matrix{T}` : An matrix containing the masses and orbital elements.
  * `elems::String` : Name of a file containing the masses and orbital elements.

Each method is simply populating the `ElementsIC.elements` field, which is a `Matrix{T}`.

# Hierarchy

  * Number of bodies: `H::Int64`: The system will be given by a 'fully-nested' Keplerian.

`H = 4` corresponds to:

```raw
3        ____|____
        |         |
2    ___|___      d
    |       |
1 __|__     c
 |     |
 a     b
```

  * Hierarchy Vector: `H::Vector{Int64}`: The first elements is the number of bodies. Each subsequent is the number of binaries on a level of the hierarchy.

`H = [4,2,1]`. Two binaries on level 1, one on level 2.

```raw
2    ____|____
    |         |
1 __|__     __|__
 |     |   |     |
 a     b   c     d
```

  * Full Hierarchy Matrix: `H::Matrix{<:Real}`: Provide the hierarchy matrix, directly.

`H = [-1 1 0 0; 0 0 -1 1; -1 -1 1 1; -1 -1 -1 -1]`. Produces the same system as `H = [4,2,1]`.
