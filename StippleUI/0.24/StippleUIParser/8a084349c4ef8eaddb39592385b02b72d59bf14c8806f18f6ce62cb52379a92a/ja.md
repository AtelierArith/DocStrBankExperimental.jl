```
prettify(html::AbstractString; level::Int = 0, indent::Union{String, Int} = 4)
```

HTMLコードを自動的な改行とインデントでフォーマットします。インデントは以下によって決定されます。

  * level: フォーマットの開始レベル; 負の値も許可されており、負のレベルはインデントされません
  * indent: 各レベルあたりの' '文字の数を示す整数または文字列値
