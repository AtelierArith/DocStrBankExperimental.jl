```
restructure(T, vals; offset = firstindex(vals) - 1) -> obj::T
```

値 `vals[offset+1:offset+n]` を型 `T` のオブジェクト `obj` に再構成します。ここで `n = struct_length(T)` は型 `T` のオブジェクトによって保存される値の総数です。

デフォルトコンストラクタは `T` に存在し、再帰的に `T` の任意の構造化フィールドにも存在しなければなりません。

[`destructure`](@ref)、[`destructure!`](@ref)、および [`struct_length`](@ref) も参照してください。

不変の具体的なオブジェクト `obj` に対して、次の同一性が成り立ちます：

```
restructure(typeof(obj), destructure(obj)) === obj
```
