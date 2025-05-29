```
constraining(f; onget=true, onset=true)
```

Create a lens to impose constraints by a callable `f`.

  * The callable `f` must be idempotent; i.e., `f ∘ f = f`.
  * If the original object already satisfies the constraint (i.e. `f(obj) == obj`), `onget=false` can be passed safely to skip calling `f` during `get`.

# Examples

```jldoctest
julia> using Kaleido, Setfield

julia> obj = (a = 1, b = 1);

julia> constraint = constraining() do obj
           @set obj.b = obj.a
       end
constraining(#1)

julia> lens = constraint ∘ @lens _.a
constraining(#1) ∘ (@lens _.a)

julia> get(obj, lens)
1

julia> set(obj, lens, 2)
(a = 2, b = 2)
```

`constraining` is useful when combined with [`@batchlens`](@ref) or [`MultiLens`](@ref):

```jldoctest
julia> using Kaleido, Setfield

julia> obj = (a = 1, b = 2, c = 3);

julia> constraint = constraining() do obj
           @set obj.c = obj.a + obj.b
       end;

julia> lens = constraint ∘ MultiLens((
           (@lens _.a),
           (@lens _.b),
       ));

julia> get(obj, lens)
(1, 2)

julia> set(obj, lens, (100, 20))
(a = 100, b = 20, c = 120)
```
