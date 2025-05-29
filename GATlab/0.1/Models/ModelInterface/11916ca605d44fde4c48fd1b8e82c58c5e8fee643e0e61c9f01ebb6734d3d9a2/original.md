Usage:

```julia
struct TypedFinSetC <: Model{Tuple{Vector{Int}, Vector{Int}}}
  ntypes::Int
end

@instance ThCategory{Vector{Int}, Vector{Int}} [model::TypedFinSetC] begin
  Ob(v::Vector{Int}) = all(1 <= j <= model.ntypes for j in v)
  Hom(f::Vector{Int}, v::Vector{Int}, w::Vector{Int}) =
     length(f) == length(v) && all(1 <= y <= length(w) for y in f)

  id(v::Vector{Int}) = collect(eachindex(v))
  compose(f::Vector{Int}, g::Vector{Int}) = g[f]

  dom(f::Vector{Int}; context) = context.dom
  codom(f::Vector{Int}; context) = context.codom
end

struct SliceCat{Ob, Hom, C <: Model{Tuple{Ob, Hom}}} <: Model{Tuple{Tuple{Ob, Hom}, Hom}}
  c::C
end

@instance ThCategory{Tuple{Ob, Hom}, Hom} [model::SliceCat{Ob, Hom, C}] where {Ob, Hom, C<:Model{Tuple{Ob, Hom}}} begin
end
```
