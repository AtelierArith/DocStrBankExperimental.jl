```
multiline(str; style=:folded, chomp=:strip) -> AbstractString
```

提供された `style` と `chomp` に従ってマルチライン文字列を操作します。YAMLのマルチライン文字列（ブロックスカラーとも呼ばれる）と同様に動作します。

# 引数

  * `str::AbstractString`: 処理されるマルチライン文字列

# キーワード

  * `style::Symbol`: 改行をスペースに置き換える（`:folded`）または改行を保持する（`:literal`）
  * `chomp::Symbol`: 終わりに改行なし（`:strip`）、終わりに単一の改行（`:clip`）、または終わりのすべての改行を保持する（`:keep`）
