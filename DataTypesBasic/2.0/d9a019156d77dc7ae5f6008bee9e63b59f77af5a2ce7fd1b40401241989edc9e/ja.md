```
getright(Identity(23)) == 23
getright(Const(:something))  # throws MethodError
```

"右側"の`Identity`値から値を抽出します。他のものに使用すると大きなエラーが発生します。`Base.get`と同じですが、サイトについて明示的であり（他のものには定義されていません）
