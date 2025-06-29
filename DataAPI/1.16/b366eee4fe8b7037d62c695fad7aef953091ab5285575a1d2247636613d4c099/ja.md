```
metadata(x, key::AbstractString, [default]; style::Bool=false)
```

オブジェクト `x` に関連付けられたメタデータ値をキー `key` に対して返します。`x` がメタデータの読み取りをサポートしていない場合や、`key` に対するマッピングがない場合はエラーをスローします。

`style=true` の場合、メタデータ値とメタデータスタイルのタプルを返します。メタデータスタイルは、`key` に対して保存されているメタデータの種類に関する追加情報です。

メタデータ `style` の使用の一つは、`x` が変換されるときにメタデータがどのように伝播されるべきかを決定することです。このインターフェースは、メタデータがどの操作の下でも伝播されるべきではないことを示す `:default` スタイルを定義します（これはソーステーブルのコピーが行われるときにのみ保持されます）。メタデータをサポートするすべてのタイプは、少なくともこのスタイルを許可します。

`default` が渡された場合、メタデータの読み取りがサポートされているが `key` に対するマッピングが欠けている場合はそれを返します。`style=true` の場合は `(default, :default)` を返します。
