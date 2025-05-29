```
dict2colmetadata!(table, dict; style::Bool=false, defaultstyle::Symbol=:default)
```

`dict`に格納された列レベルのメタデータを`table`に格納します（以前に存在していたすべての列レベルのメタデータは破棄されます）。

`style`キーワード引数は、`dict`にスタイル情報が含まれているかどうかを示します（デフォルトは`false`）。`style`が`false`の場合、メタデータスタイルを設定する際に`defaultstyle`（デフォルトは`:default`）が使用されます。スタイルが渡されると、それは任意の値にすることができますが、内部的には`Symbol`に変換されます。

この関数は、`dict`がキーと値のペアを格納していると仮定しています。ここで、キーは列名であり、値はメタデータのキーと値のペアを格納する辞書です。これは通常、`colmetadata`関数によって以前に生成されたものです。

参照: [`dict2metadata!`](@ref)
