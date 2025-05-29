```
calmax(x)
calmax!(x, val)
```

表示目的のための最大要素を指定します。指定されていない場合は、コレクション内の最大値を返します。

## 例

```jldoctest
julia> using FieldProperties

julia> x = reshape(1:16, 4, 4);

julia> calmax(x)
16

julia> struct ArrayMaxThresh{T,N}
           a::AbstractArray{T,N}
           calmax::T
       end

julia> calmax(ArrayMaxThresh(x, 10))
10
```
