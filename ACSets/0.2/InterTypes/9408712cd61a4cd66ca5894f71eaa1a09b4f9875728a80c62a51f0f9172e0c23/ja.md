型を表すインタタイプ式。

TODO: ジェネリック型 TODO: 匿名和、匿名積を削除 TODO: プリミティブを分離し、これを次のようにする

```julia
@data InterType begin
  PrimType(prim::InterTypePrimitive)
  TypeRef(path::RefPath)
  TypeApp(type::InterType, args::Vector{InterType})
end
```
