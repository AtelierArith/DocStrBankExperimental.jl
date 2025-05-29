`canonicalize(template, input::NamedTuple)`

テンプレートに従って入力のNamedTupleを正準化します。構造体のインスタンスを返します。

テンプレート内のすべての値はデフォルト値として使用されます。

# 例

```julia-repl
julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end

julia> template = AStruct((0,0), (0.,0.), missing);

julia> canonicalize(template, (xr=(1,2),))
AStruct((1, 2), (0.0, 0.0), missing)

julia> canonicalize(template, (yr=(1,2), xr=(3.3, 4.4), tit="Foo"))
AStruct((3.3, 4.4), (1, 2), "Foo")
```
