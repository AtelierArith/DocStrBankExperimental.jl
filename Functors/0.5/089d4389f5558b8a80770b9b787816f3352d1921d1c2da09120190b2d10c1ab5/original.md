```
fmap(f, x, ys...; exclude = Functors.isleaf, walk = Functors.DefaultWalk(), [prune])
```

A structure and type preserving `map`.

By default it transforms every leaf node (identified by `exclude`, default [`isleaf`](@ref Functors.isleaf)) by applying `f`, and otherwise traverses `x` recursively using [`functor`](@ref Functors.functor). Optionally, it may also be associated with objects `ys` with the same tree structure. In that case, `f` is applied to the corresponding leaf nodes in `x` and `ys`.

See also [`fmap_with_path`](@ref) and [`fmapstructure`](@ref).

# Examples

```jldoctest
julia> fmap(string, (x=1, y=(2, 3)))
(x = "1", y = ("2", "3"))

julia> nt = (a = [1,2], b = [23, (45,), (x=6//7, y=())], c = [8,9]);

julia> fmap(println, nt)
[1, 2]
23
45
6//7
()
[8, 9]
(a = nothing, b = Any[nothing, (nothing,), (x = nothing, y = nothing)], c = nothing)

julia> fmap(println, nt; exclude = x -> x isa Array)
[1, 2]
Any[23, (45,), (x = 6//7, y = ())]
[8, 9]
(a = nothing, b = nothing, c = nothing)

julia> twice = [1, 2];  # println only acts once on this

julia> fmap(println, (i = twice, ii = 34, iii = [5, 6], iv = (twice, 34), v = 34.0))
[1, 2]
34
[5, 6]
34
34.0
(i = nothing, ii = nothing, iii = nothing, iv = (nothing, nothing), v = nothing)

julia> d1 = Dict("x" => [1,2], "y" => 3);

julia> d2 = Dict("x" => [4,5], "y" => 6, "z" => "an_extra_value");

julia> fmap(+, d1, d2) == Dict("x" => [5, 7], "y" => 9) # Note that "z" is ignored
true
```

Mutable objects which appear more than once are only handled once (by caching `f(x)` in an `IdDict`). Thus the relationship `x.i === x.iv[1]` will be preserved. An immutable object which appears twice is not stored in the cache, thus `f(34)` will be called twice, and the results will agree only if `f` is pure.

By default, almost all container-like types have children to recurse into.  Arrays of numbers do not.

To opt out of recursion for custom types use [`@leaf`](@ref) or pass a custom `exclude` function.

```jldoctest withfoo
julia> struct Foo; x; y; end

julia> struct Bar; x; end

julia> m = Foo(Bar([1,2,3]), (4, 5, Bar(Foo(6, 7))));

julia> fmap(x -> 10x, m)
Foo(Bar([10, 20, 30]), (40, 50, Bar(Foo(60, 70))))

julia> fmap(string, m)
Foo(Bar("[1, 2, 3]"), ("4", "5", Bar(Foo("6", "7"))))

julia> fmap(string, m, exclude = v -> v isa Bar)
Foo("Bar([1, 2, 3])", (4, 5, "Bar(Foo(6, 7))"))
```

To recurse into custom types without reconstructing them afterwards, use [`fmapstructure`](@ref).

For advanced customization of the traversal behaviour, pass a custom `walk` function that subtypes [`Functors.AbstractWalk`](@ref). The call `fmap(f, x, ys...; walk = mywalk)` will wrap `mywalk` in [`ExcludeWalk`](@ref) then [`CachedWalk`](@ref). Here, [`ExcludeWalk`](@ref) is responsible for applying `f` at excluded nodes. For a low-level interface for executing a user-constructed walk, see [`execute`](@ref).

```jldoctest withfoo
julia> struct MyWalk <: Functors.AbstractWalk end

julia> (::MyWalk)(recurse, x) = x isa Bar ? "hello" :
                                            Functors.DefaultWalk()(recurse, x)

julia> fmap(x -> 10x, m; walk = MyWalk())
Foo("hello", (40, 50, "hello"))
```

The behaviour when the same node appears twice can be altered by giving a value to the `prune` keyword, which is then used in place of all but the first:

```jldoctest
julia> twice = [1, 2];

julia> fmap(float, (x = twice, y = [1,2], z = twice); prune = missing)
(x = [1.0, 2.0], y = [1.0, 2.0], z = missing)
```
