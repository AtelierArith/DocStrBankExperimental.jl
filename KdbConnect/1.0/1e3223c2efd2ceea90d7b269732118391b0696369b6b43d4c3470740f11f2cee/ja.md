```
execute(hobj::KdbHandle, query::AbstractString, args...)
execute(conn::KdbConnectionInfo, query::AbstractString, args...)
```

オープンな接続ハンドル `hobj::KdbHandle` を介して KDB インスタンスでクエリを実行します。最初の引数が `KdbConnectionInfo` の場合、一時的なハンドルが自動的にオープンされ、クローズされます。クエリは文字列とオプションの `args` で構成され、これらは KDB インスタンスに送信されます。

例:

```
    execute(hobj,"1+1")
    execute(hobj,"{x+y}", π-3, 3)
    execute(hobj,"{0N!x}","Hello from KDB!")
    execute(conn, "([] w:10?(0nj,til 3) ;x:10?1f ; y:10?(12;1b;`foo;"bar") ; z:10?`3)")
```
