```
pack(value, [, ctx::Context])::Vector{UInt8}
pack(value, [, fmt::Format, ctx::Context])::Vector{UInt8}
pack(io::IO, args...)::Nothing
```

`value`のバイナリmsgpack表現を、指定されたフォーマット`fmt`に従って作成します。ストリーム`io`が渡された場合、表現はそこに書き込まれます。

フォーマットが提供されていない場合、`format(typeof(value), ctx)`を介して`value`の型から導出されます。コンテキストは、julia 1.11以降のスコープ付き値である[`context`](@ref)の値にデフォルト設定され、そうでない場合は参照されます。

フォーマットとコンテキストの両方が提供されている場合、`fmt`は`value`のパッキングに使用され、`ctx`はより深いパッキング関連の呼び出しに渡されます。
