`canonicalize(template::DataType, input::NamedTuple)`

テンプレートに従って入力のNamedTupleを正準化します。構造体のインスタンスを返します。

`input`がテンプレートで必要とされる値よりも少ない値を含む場合、`missing`値を持つ構造体を作成しようとします。構造体の定義でこれが禁止されている場合、エラーが発生します。

# 例

```julia-repl
julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end

julia> canonicalize(AStruct, (xr=(1,2), yr=(3,4.)))
AStruct((1, 2), (3, 4.0), missing)

julia> canonicalize(AStruct, (xr=(1,2), yr=(3,4.), tit="Foo"))
AStruct((1, 2), (3, 4.0), "Foo")
```
