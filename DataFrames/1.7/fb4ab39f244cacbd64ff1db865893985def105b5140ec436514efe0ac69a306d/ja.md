```
DataFrameColumns{<:AbstractDataFrame}
```

`AbstractDataFrame`の列を反復処理することを可能にするベクトルのようなオブジェクトです。

整数、`Symbol`、または文字列を使用して`DataFrameColumns`オブジェクトにインデックスを付けると、対応する列が返されます（コピーなし）。複数の列セレクタを使用して`DataFrameColumns`オブジェクトにインデックスを付けると、選択された列のみを含む新しい親を持つ部分的な`DataFrameColumns`オブジェクトが返されます（コピーなし）。

`DataFrameColumns`はほとんどの`AbstractVector` APIをサポートしています。主な違いは、読み取り専用であり、`keys`関数が`Symbol`のベクトルを返すこと（通常のベクトルの場合は整数ではなく）です。

特に、`findnext`、`findprev`、`findfirst`、`findlast`、および`findall`関数がサポートされており、`findnext`および`findprev`関数では整数、文字列、または`Symbol`を参照インデックスとして渡すことが許可されています。
