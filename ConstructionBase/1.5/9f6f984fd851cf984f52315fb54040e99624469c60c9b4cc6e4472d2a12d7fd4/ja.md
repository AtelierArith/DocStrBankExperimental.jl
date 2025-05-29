```
constructorof(T::Type) -> constructor
```

オブジェクト `constructor` を返します。これは、フィールド値から型 `T` のオブジェクトを構築するために使用できます。通常、`constructor` はすべてのパラメータが削除された型 `T` になります：

```jldoctest
julia> using ConstructionBase

julia> struct T{A,B}
           a::A
           b::B
       end

julia> constructorof(T{Int,Int})
T
```

ただし、`constructor` が型であることは保証されていません：

```jldoctest; setup = :(using ConstructionBase)
julia> struct S
           a
           b
           checksum
           S(a,b) = new(a,b,a+b)
       end

julia> ConstructionBase.constructorof(::Type{<:S}) =
           (a, b, checksum=a+b) -> (@assert a+b == checksum; S(a,b))

julia> constructorof(S)(1,2)
S(1, 2, 3)

julia> constructorof(S)(1,2,4)
ERROR: AssertionError: a + b == checksum
```

代わりに、`constructor` は次のプロパティを満たす任意のオブジェクトである可能性があります：

  * [`getfields`](@ref) の要素からオブジェクトを再構築できる必要があります：

```julia
ctor = constructorof(typeof(obj))
@assert obj == ctor(getfields(obj)...)
@assert typeof(obj) == typeof(ctor(getfields(obj)...))
```

  * 可能な限り多くの `args` の値に対して、逆方向も成り立つ必要があります：

```julia
ctor = constructorof(T)
getfields(ctor(args...)) == args
```

たとえば、適切なパラメトリック型が与えられた場合、そのフィールドの型を変更することができるはずです：

```jldoctest; setup = :(using ConstructionBase)
julia> struct T{A,B}
           a::A
           b::B
       end

julia> t = T(1,2)
T{Int64, Int64}(1, 2)

julia> constructorof(typeof(t))(1.0, 2)
T{Float64, Int64}(1.0, 2)

julia> constructorof(typeof(t))(10, 2)
T{Int64, Int64}(10, 2)
```

`constructorof` は [the raw level](@ref the-raw-level) に属します。`constructorof` は、名前に `gensym` `#` を持つコンストラクタがないすべての匿名 `Function` に対して生成されます。`gensym` 名を持つカスタム構造体 `<: Function` は、手動で `constructorof` を定義する必要があるかもしれません。

詳細は [Tips section in the manual](@ref type-tips) を参照してください。
