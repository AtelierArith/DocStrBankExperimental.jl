```
@def_pprint [properties=nothing] [mime_types=nothing] [generic_mime=false] [base_show=false] T
```

型 `T` およびオプションで提供された `mime_types` のための美しい印刷メソッドを自動生成します。

# 引数

  * `properties=nothing`: `x::T` から使用するプロパティに対応する `Symbol` または `Symbol` のベクトル式。指定されていない場合は `x` のフィールド名を使用するのがデフォルトです。
  * `mime_types=nothing`: 生成する `MIME` タイプ。もしこの値が空文字列であれば、MIME タイプは生成されません。この値が非空の `String` または `String` のベクトルまたはタプル式であれば、これらの MIME タイプがコード生成時に使用されます。それ以外の場合、この値が `nothing` であれば、生成されるコードは以前に `@mime_type` で登録された MIME タイプを使用します。
  * `generic_mime::Bool=false`: `true` の場合、`mime_types` の入力を無視し、すべてのコード生成に対して一般的（テンプレート化されていない）MIME タイプを使用します。
  * `base_show::Bool=false`: `true` の場合、`mime_types` の各 `mime` に対して `Base.show(io::IO, ::MIME(mime), ::T)` を定義します。
