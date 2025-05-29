```
ustrip(u::Units, x::Quantity)
ustrip(T::Type, u::Units, x::Quantity)
```

`x`を[`uconvert`](@ref)を使用して単位`u`に変換し、結果の量の前にある数値を返します。`T`が指定されている場合、結果の数値も型`T`に`convert`します。

この関数は、量を処理する方法を知らないパッケージとの互換性を主に目的としています。

```jldoctest
julia> ustrip(u"m", 1u"mm") == 1//1000
true

julia> ustrip(Float64, u"m", 2u"mm") == 0.002
true
```

`ustrip`は`InverseFunctions.inverse`をサポートしています：

```jldoctest
julia> using InverseFunctions: inverse

julia> inverse(Base.Fix1(ustrip, u"m"))(5)
5 m
```
