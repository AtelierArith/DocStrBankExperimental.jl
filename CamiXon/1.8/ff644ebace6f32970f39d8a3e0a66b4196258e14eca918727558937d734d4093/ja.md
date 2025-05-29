```
castNamedValue(val::Value; name=" ", comment=" ")
```

[`NamedValue`](@ref) オブジェクトを作成するためのメソッド

#### 例

```
julia> v = Value(1.602176634e-19, "C");

julia> nv = castNamedValue(v; name="e");

julia> nv.name * " = " * strValue(nv.val)
"e = 1.60218e-19 C"
```
