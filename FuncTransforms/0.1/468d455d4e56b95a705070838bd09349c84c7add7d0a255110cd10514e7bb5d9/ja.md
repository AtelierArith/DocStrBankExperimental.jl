```
VA(name::Symbol, drop::Int; gen = true)
```

「VarArg」。`VA`を使用すると、この引数の値を変換された関数の引数に割り当てることができます。`drop`は、変換された関数の指定された数の引数を削除します（`var"#self#"`もカウントされます）。
