```
to(SomeArray, ::OtherArray)::SomeArray
```

`OtherArray`のインスタンスから`SomeArray`のインスタンスを構築します。

# 例

```jldoctest
julia> using AxisArrayConversion: SimpleAxisArray, to

julia> to(SimpleAxisArray, (axes=(a=1:3,), values=[10,20,30]))
SimpleAxisArray(axes = (a = 1:3,), values = [10, 20, 30])

julia> arr = to(SimpleAxisArray, (axes=(a=1:3,), values=[10,20,30]))
SimpleAxisArray(axes = (a = 1:3,), values = [10, 20, 30])

julia> to(NamedTuple, arr)
(axes = (a = 1:3,), values = [10, 20, 30])

julia> to(NamedTuple, [1 2; 3 4])
(axes = (x1 = Base.OneTo(2), x2 = Base.OneTo(2)), values = [1 2; 3 4])
```

この関数はオーバーロードすべきではありません。代わりに[`namedtuple`](@ref)と[`from_namedtuple`](@ref)をオーバーロードするべきです。

この関数は公開APIの一部であり、SemVerの保証の対象です。
