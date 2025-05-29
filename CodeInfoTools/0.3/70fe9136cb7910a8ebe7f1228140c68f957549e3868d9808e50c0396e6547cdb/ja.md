```
return!(b::Builder, v::Variable)
return!(b::Builder, v::NewVariable)
```

`b.to::Canvas`の現在の末尾に`Core.ReturnNode`をプッシュします。ユーザーが`v::Variable`または`v::NewVariable`インスタンスを渡す必要があるため、`Core.ReturnNode`を作成する前に正しいアンパック/タプル化を行ってください。
