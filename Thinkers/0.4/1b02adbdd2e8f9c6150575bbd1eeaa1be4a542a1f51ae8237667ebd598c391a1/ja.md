```
Thunk(callable, args...; kwargs...)
```

遅延評価のために呼び出し可能なオブジェクトとその引数を保持します。評価するには `reify!` を使用します。

# 例

```jldoctest
julia> using Thinkers

julia> a = Thunk(x -> 3x, 4);

julia> reify!(a);

julia> getresult(a)
Some(12)

julia> b = Thunk(+, 4, 5);

julia> reify!(b);

julia> getresult(b)
Some(9)

julia> c = Thunk(sleep, 1);

julia> getresult(c)  # `c` はまだ評価されていません

julia> reify!(c);  # `c` は評価されました

julia> getresult(c)
Some(nothing)

julia> f(args...; kwargs...) = collect(kwargs);

julia> d = Thunk(f, 1, 2, 3; x=1.0, y=4, z="5");

julia> reify!(d);

julia> getresult(d)
Some(Pair{Symbol, Any}[:x => 1.0, :y => 4, :z => "5"])

julia> e = Thunk(sin, "1");  # エラーをキャッチ

julia> reify!(e);

julia> haserred(e)
true
```
