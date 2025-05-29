```
MultiRow(n::Int, vpos::Symbol, cell::Any, width::String)
MultiRow(n, vpos, cell; width="*")
```

`\multirow[vpos]{n}{width}{cell}`のために、`vpos`には`:t`、`:c`、`:b`のシンボルを使用します。
