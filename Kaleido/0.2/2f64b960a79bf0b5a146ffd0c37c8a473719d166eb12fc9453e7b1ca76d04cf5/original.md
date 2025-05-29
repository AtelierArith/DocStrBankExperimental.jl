```
@batchlens begin
    lens_expression_1
    lens_expression_2
    ...
    lens_expression_n
end
```

From $n$ "lens expression", create a lens that gets/sets $n$-tuple. Each "lens expression" is an expression that is supported by `Setfield.@lens` or such expression post-composed with other lenses using `∘`.

See also [`batch`](@ref) which does all the heavy lifting of the transformation of the lenses.

# Examples

```jldoctest
julia> using Kaleido, Setfield

julia> lens = @batchlens begin
           _.a.b.c
           _.a.b.d ∘ converting(fromfield = x -> parse(Int, x), tofield = string)
           _.a.e
       end;

julia> obj = (a = (b = (c = 1, d = "2"), e = 3),);

julia> get(obj, lens)
(1, 2, 3)

julia> set(obj, lens, (10, 20, 30))
(a = (b = (c = 10, d = "20"), e = 30),)
```
