```julia
construct_railfence(input::AbstractString, n_rails::Integer)
construct_railfence(input::AbstractArray{T}, n_rails::Integer) where {T <: Number}
```

See [`https://en.wikipedia.org/wiki/Rail_fence_cipher`](https://en.wikipedia.org/wiki/Rail_fence_cipher).

---

### Examples

```julia
julia> construct_railfence("WE ARE DISCOVERED. FLEE AT ONCE", 3)
3×26 Array{Char,2}:
 'W'  '□'  '□'  '□'  'E'  '□'  '□'  '□'  'C'  '□'  '□'  '□'  'R'  …  '□'  '□'  'F'  '□'  '□'  '□'  'A'  '□'  '□'  '□'  'C'  '□'
 '□'  'E'  '□'  'R'  '□'  'D'  '□'  'S'  '□'  'O'  '□'  'E'  '□'     '□'  '.'  '□'  'L'  '□'  'E'  '□'  'T'  '□'  'N'  '□'  'E'
 '□'  '□'  'A'  '□'  '□'  '□'  'I'  '□'  '□'  '□'  'V'  '□'  '□'     'D'  '□'  '□'  '□'  'E'  '□'  '□'  '□'  'O'  '□'  '□'  '□'
```
