```
ext(path) -> String or nothing
```

パスの拡張子を返します。`Base.splitext(s)[2]`と似た動作をしますが、先頭の '.' は保持しません。

元の `splitext`:

  * "myfile.txt"    -> ".txt"
  * "myfile."       -> "."
  * "myfile"        -> ""
  * ".myfile"       -> ""
  * "."             -> ""

新しい `ext`:

  * "myfile.txt"    -> "txt"
  * "myfile."       -> ""
  * "myfile"        -> nothing
  * ".myfile"       -> nothing
  * "."             -> nothing

`exty`、`hasext` も参照してください。
