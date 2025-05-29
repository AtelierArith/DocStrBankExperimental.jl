```
ExtendScheme(s, [h=nothing])
```

Functor for extending a scheme, `s`, through the addition on a transformation, `h`, which constructs the index respective to each element on which it is called. It may be called directly, as shown below, but is most commonly passed to `tile` or `tiles`.

See also: [`Scheme`](@ref), [`@scheme`](@ref)

# Examples

```jldoctest
julia> s = Scheme(sum, last);

julia> e = ExtendScheme(s, abs2 ∘ last);

julia> e([1, 2, 3])
((6, 3), 9)

julia> ExtendScheme(s)([1, 2, 3]) == s([1, 2, 3])
true

julia> e2 = ExtendScheme(e, first);

julia> e2([1, 2, 3])
(((6, 3), 9), 1)

julia> ExtendScheme(e)([1, 2, 3]) == e([1, 2, 3])
true
```
