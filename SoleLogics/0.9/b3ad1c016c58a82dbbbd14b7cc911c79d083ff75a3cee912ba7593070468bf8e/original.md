```
accessibles(
    fr::AbstractMultiModalFrame{W},
    w::W,
    r::AbstractRelation
) where {W<:AbstractWorld}
```

Return the worlds in frame `fr` that are accessible from world `w` via relation `r`.

# Examples

```julia-repl
julia> fr = SoleLogics.FullDimensionalFrame((10,),);

julia> typeof(accessibles(fr, Interval(2,5), IA_L))
Base.Generator{...}

julia> typeof(accessibles(fr, globalrel))
Base.Generator{...}

julia> @assert SoleLogics.nworlds(fr) == length(collect(accessibles(fr, globalrel)))

julia> typeof(accessibles(fr, Interval(2,5), identityrel))
Vector{Interval{Int64}}

julia> Interval(8,11) in collect(accessibles(fr, Interval(2,5), IA_L))
true
```

# Implementation

Since `accessibles` always returns an iterator of worlds of the same type `W`, the current implementation of `accessibles` for multi-modal frames delegates the enumeration to a lower level `_accessibles` function, which returns an iterator of parameter tuples that are, then, fed to the world constructor the using IterTools generators, as in:

```
function accessibles(
    fr::AbstractMultiModalFrame{W},
    w::W,
    r::AbstractRelation,
) where {W<:AbstractWorld}
    IterTools.imap(W, _accessibles(fr, w, r))
end
```

As such, when defining new frames, worlds, and/or relations, one should provide new methods for `_accessibles`. For example:

```
_accessibles(fr::Full1DFrame, w::Interval{<:Integer}, ::_IA_A) = zip(Iterators.repeated(w.y), w.y+1:X(fr)+1)
```

This pattern is generally convenient; it can, however, be bypassed, although this requires defining two additional methods in order to resolve dispatch ambiguities. When defining a new frame type `FR{W}`, one can resolve the ambiguities and define a custom `accessibles` method by providing these three methods:

```
# access worlds through relation `r`
function accessibles(
    fr::FR{W},
    w::W,
    r::AbstractRelation,
) where {W<:AbstractWorld}
    ...
end

# access current world
function accessibles(
    fr::FR{W},
    w::W,
    r::IdentityRel,
) where {W<:AbstractWorld}
    [w]
end

# access all worlds
function accessibles(
    fr::FR{W},
    w::W,
    r::GlobalRel,
) where {W<:AbstractWorld}
    allworlds(fr)
end
```

In general, it should be true that `collect(accessibles(fr, w, r)) isa AbstractWorlds{W}`.

See also [`AbstractWorld`](@ref), [`AbstractRelation`](@ref), [`AbstractMultiModalFrame`](@ref).
