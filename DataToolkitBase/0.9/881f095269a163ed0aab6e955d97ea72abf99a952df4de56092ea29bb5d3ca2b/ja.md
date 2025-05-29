```
help(r::ReplCmd)
```

`r`のヘルプ文字列を表示します。

```
help(r::ReplCmd{<:Any, Vector{ReplCmd}})
```

`r`のヘルプ文字列とサブコマンドテーブルを表示します。
