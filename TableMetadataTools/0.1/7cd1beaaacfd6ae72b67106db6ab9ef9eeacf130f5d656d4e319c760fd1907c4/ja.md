```
dict2metadata!(table, dict; style::Bool=false, defaultstyle::Symbol=:default)
```

`dict`に格納されたテーブルレベルのメタデータを`table`に格納します（以前に存在していたすべてのテーブルレベルのメタデータは破棄されます）。

`style`キーワード引数は、`dict`にスタイル情報が含まれているかどうかを示します（デフォルトは`false`）。`style`が`false`の場合、メタデータスタイルを設定する際に`defaultstyle`（デフォルトは`:default`）が使用されます。スタイルが渡されると、それは任意の値にすることができますが、内部的には`Symbol`に変換されます。

この関数は、`dict`がキーと値のメタデータを格納していると仮定しています。これは通常、`metadata`関数によって以前に生成されたものです。

参照: [`dict2colmetadata!`](@ref)
