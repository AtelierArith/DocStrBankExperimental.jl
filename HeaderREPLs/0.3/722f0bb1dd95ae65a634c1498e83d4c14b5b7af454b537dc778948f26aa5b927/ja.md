```
print_header(io::IO, header::CustomHeader)
```

`header`を`io`に出力します。`header`は`nlines`というフィールドを含む可変構造体でなければなりません。`print_header`を終了する前に、このフィールドをヘッダーの表示に占められた行数に設定する必要があります。

`print_header`を定義する必要がありますが、一般的には直接呼び出すべきではありません。ヘッダーを表示する必要がある場合は、`refresh_header`を呼び出してください。
