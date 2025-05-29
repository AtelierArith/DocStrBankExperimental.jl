`complementInt(full::Matrix{<:Integer}, sub::Matrix{<:Integer})`

`complementInt(sub::Matrix{<:Integer})`

Let `M` be the integral row space of `full` and let `S` be the integral row space   of  `sub`,  which  should  be  a  subspace  of  `M`.  The  function `complementInt` computes a free basis for `M` that extends `S`, that is, if the dimension of `S` is `n` it determines a basis `B={b₁,…,bₘ}` for `M`, as well as `n` integers `x₁,…,xₙ` such that the `n` vectors `sᵢ:=xᵢ⋅bᵢ` form a basis  for `S`. If only one argument is  given, `full` is assumed to be the identity matrix of size `size(sub,2)`.

The  function  `complementInt`  returns  a  named  tuple with the following components:

  * `complement` a matrix whose rows are `bₙ₊₁,…,bₘ`.
  * `sub` a matrix whose rows are the `sᵢ` (a basis for `S`).
  * `moduli` the factors `xᵢ`.

```julia-repl
julia> n=[1 2 3;4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> complementInt(n)
(complement = [0 0 1], sub = [1 2 3; 0 3 6], moduli = [1, 3])
```
