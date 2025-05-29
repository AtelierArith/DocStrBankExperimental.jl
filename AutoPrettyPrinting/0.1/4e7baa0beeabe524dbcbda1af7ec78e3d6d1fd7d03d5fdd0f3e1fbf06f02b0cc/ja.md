```
@def_pprint_atomic [to_string=nothing] [mime_types=nothing] [generic_mime=false] T
```

型 `T` を原子的な型（すなわち、サブフィールドやサブ要素を持たない型）として登録し、各 `mime` タイプに対して `custom_tile(x::T, mime::MIME{S}) = to_string(x)` を定義します。

# 引数

  * `to_string=nothing`: `x` の文字列表現を返す関数式。提供されない場合はデフォルトで `Base.string` が使用されます。
  * `mime_types=nothing`: 生成する `MIME` タイプ。もしこの値が空文字列であれば、MIME タイプは生成されません。この値が非空の `String` または `String` の `vect` または `tuple` 表現であれば、これらの MIME タイプがコード生成時に使用されます。それ以外の場合、この値が `nothing` であれば、生成されるコードは以前に `@mime_type` で登録された MIME タイプを使用します。
  * `generic_mime::Bool=false`: `true` の場合、`mime_types` の入力を無視し、すべてのコード生成に対して一般的（テンプレート化されていない）MIME タイプを使用します。
