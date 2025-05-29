`canonicalize(template, input::Tuple)`

テンプレートに従って入力タプルを正準化します。`template`の型に応じて、NamedTupleまたは構造体のインスタンスを返します。入力タプルはテンプレートと同じ数の要素を持っている必要があります。

# 例

```julia-repl
julia> template = (xrange=NTuple{2,Number},
                   yrange=NTuple{2,Number},
                   title="Default string");

julia> canonicalize(template, ((1,2), (3, 4.), "Foo"))
(xrange = (1, 2), yrange = (3, 4.0), title = "Foo")

julia> struct AStruct
           xrange::NTuple{2, Number}
           yrange::NTuple{2, Number}
           title::Union{Missing, String}
       end;

julia> canonicalize(AStruct, ((1,2), (3, 4.), "Foo"))
AStruct((1, 2), (3, 4.0), "Foo")

julia> template = AStruct((0,0), (0.,0.), missing);

julia> canonicalize(template, ((1,2), (3, 4.), "Foo"))
AStruct((1, 2), (3, 4.0), "Foo")
```
