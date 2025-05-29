```
@convert_to PerlType argument
```

このマクロは、[`@pm`](@ref)マクロとPolymakeの`common.convert_to`メソッドを使用してオブジェクトを迅速に変換するために使用できます。後者はPerlに基づいているため、指定された型もPolymakeのPerlによって理解可能である必要があります。

# 例

```jldoctest
julia> @convert_to Integer true
1

julia> @convert_to Array{Set{Int}} [Set([1, 2, 4, 5, 7, 8]), Set([1]), Set([6, 9])]
pm::Array<pm::Set<long, pm::operations::cmp>>
{1 2 4 5 7 8}
{1}
{6 9}


julia> @convert_to Vector{Float} [10, 11, 12]
pm::Vector<double>
10 11 12

julia> @convert_to Matrix{Rational} [10/1 11/1 12/1]
pm::Matrix<pm::Rational>
10 11 12

```
