このモジュールは、新しいタイプの `AbstractString` である `StringView` を実装しており、UTF-8 エンコードされた Unicode データとして解釈される任意のバイト配列（任意の `AbstractVector{UInt8}`）の文字列表現を提供します。

Julia の組み込み `String` タイプ（これも UTF-8 データをラップします）とは異なり、`StringView` タイプは *任意の* `AbstractVector{UInt8}` インスタンスのコピーなしのラップであり、配列の「所有権」を持たず、変更もしません。その他の場合、`StringView` は、`String` を使用していたかもしれない任意のコンテキストで使用できることを意図しています。
