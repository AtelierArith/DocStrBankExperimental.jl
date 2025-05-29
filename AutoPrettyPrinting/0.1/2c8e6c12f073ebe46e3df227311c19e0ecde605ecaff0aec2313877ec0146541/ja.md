```
@custom_tile [mime_types=nothing] [generic_mime=false] [base_show=false] T => custom_tile_expr
```

タイプ `T` のカスタムタイルメソッド定義を作成し、オプションで提供された `mime_types` を使用して `custom_tile_expr` を関数の本体として使用します。

# 引数

  * `mime_types=nothing`: 生成する `MIME` タイプ。 この値が空文字列の場合、MIME タイプは生成されません。この値が非空の `String` または `String` の `vect` または `tuple` 式の場合、これらの MIME タイプがコード生成時に使用されます。それ以外の場合、この値が `nothing` の場合、生成されるコードは以前に `@mime_type` で登録された MIME タイプを使用します。
  * `generic_mime::Bool=false`: `true` の場合、`mime_types` の入力を無視し、すべてのコード生成に対して一般的（テンプレート化されていない）MIME タイプを使用します。
  * `base_show::Bool=false`: `true` の場合、`mime_types` の各 `mime` に対して `Base.show(io::IO, ::MIME(mime), ::T)` を定義します。
  * `custom_tile_expr`: `custom_tile` メソッドの本体として使用される式。この値が `block` 式の場合、タイプ `T` のオブジェクトを示す `_obj_` プレースホルダーと MIME タイプを示す `_mime_` プレースホルダーを含む必要があります。それ以外の場合、形式 `(object, mime_type)->expr` の関数定義式であることができます。
