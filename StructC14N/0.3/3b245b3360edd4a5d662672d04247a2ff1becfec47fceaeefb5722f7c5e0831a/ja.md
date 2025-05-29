`canonicalize(template::NamedTuple, input::NamedTuple)`

NamedTuple テンプレートに従って入力 NamedTuple を正準化します。 NamedTuple を返します。

デフォルト値は `template` で指定する必要があります。 デフォルト値を指定しないようにするには、対応するアイテムを `Type` オブジェクトにする必要があり、そのデフォルト値は `missing` になります（`input` で上書きされない限り）。

# 例

```julia-repl
julia> template = (xrange=NTuple{2, Number},
                   yrange=NTuple{2, Number},
                   title="Default string");

julia> c = canonicalize(template, (xr=(1,2),))
(xrange = (1, 2), yrange = missing, title = "Default string")

julia> c = canonicalize(template, (xr=(1,2), yrange=(3, 4.), tit="Foo"))
(xrange = (1, 2), yrange = (3, 4.0), title = "Foo")
```
