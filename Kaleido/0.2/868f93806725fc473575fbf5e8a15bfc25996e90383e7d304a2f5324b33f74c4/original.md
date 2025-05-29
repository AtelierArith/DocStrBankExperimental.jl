```
batch(lens₁, lens₂, ..., lensₙ) :: Lens
```

From $n$ lenses, create a single lens that gets/sets $n$-tuple in such a way that the number of call to the constructor is minimized. This is done by calling [`IndexBatchLens`](@ref) whenever possible.

# Examples

```jldoctest
julia> using Kaleido, Setfield

julia> lens = @batchlens begin
           _.a.b.c
           _.a.b.d
           _.a.e
       end;

julia> @assert lens ==
           IndexBatchLens(:a) ∘ MultiLens((
               (@lens _[1]) ∘ IndexBatchLens(:b, :e) ∘ MultiLens((
                   (@lens _[1]) ∘ IndexBatchLens(:c, :d),
                   (@lens _[2]) ∘ Kaleido.SingletonLens(),
               )) ∘ FlatLens(2, 1),
           )) ∘ FlatLens(3)

julia> obj = (a=(b=(c=1, d=2), e=3),);

julia> get(obj, lens)
(1, 2, 3)

julia> set(obj, lens, (10, 20, 30))
(a = (b = (c = 10, d = 20), e = 30),)
```
