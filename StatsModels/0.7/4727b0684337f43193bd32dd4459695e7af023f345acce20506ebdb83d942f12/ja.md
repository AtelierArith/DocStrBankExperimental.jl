```
termnames(term::AbstractTerm)
```

項に関連付けられた統計変数の名前を返します。

返り値は、関連付けられた変数がない場合（例：`termnames(InterceptTerm{false}())`）は、`String`、`String`の反復可能な集合、または空のベクターのいずれかです。
