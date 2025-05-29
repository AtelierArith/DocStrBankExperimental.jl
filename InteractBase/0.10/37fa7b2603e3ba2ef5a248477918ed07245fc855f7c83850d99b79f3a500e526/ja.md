`alert(text="")`

`Widget{:alert}`を作成します。アラートをトリガーするには、次のようにします：

```julia
wdg = alert("Error!")
wdg()
```

文字列を使って`wdg`を呼び出すと、その文字列にアラートメッセージが設定され、アラートがトリガーされます：

```julia
wdg = alert("Error!")
wdg("New error message!")
```

JavaScriptが機能するためには、ウィジェットがUIの一部である必要がありますが、目に見えない場合でも構いません。
