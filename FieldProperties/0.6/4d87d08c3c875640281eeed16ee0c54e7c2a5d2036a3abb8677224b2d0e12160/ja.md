```
calmin(x)
calmin!(x, val)
```

表示目的のための最小要素を指定します。指定されていない場合は、コレクション内の最小値を返します。

## 例

```jldoctest
julia> using FieldProperties

julia> x = reshape(1:16, 4, 4);

julia> calmin(x)
1

julia> struct ArrayMinThresh{T,N}
           a::AbstractArray{T,N}
           calmin::T
       end

julia> calmin(ArrayMinThresh(x, 5))
5
```
