```
allow_unicode(allowed::Bool; temporary::Bool=false) -> Bool
```

ユニコード文字が整形表示で許可されるかどうかを設定し、以前の値を返します。`temporary`が`true`の場合、変更は現在のワーカーとセッションのみに有効です。それ以外の場合、変更は設定に永続的に保存されます。永続的な変更は常に一時的な変更を上書きします。

この関数は、`with_unicode` doブロックのスコープ内から呼び出された場合、任意の動作をする可能性があります。

関連情報として、[`is_unicode_allowed`](@ref)および[`with_unicode`](@ref)を参照してください。
