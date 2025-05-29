`preferred_text( named_tuple [; language]  )` 言語コードと対応するテキストの名前付きタプルを受け取ります。現在選択されている言語のテキストを返します。現在の言語のテキストが提供されていない場合は、名前付きタプルの最初の値を返します。

例:    `preferred_text( (en="Hello", de="Hallo") )`
