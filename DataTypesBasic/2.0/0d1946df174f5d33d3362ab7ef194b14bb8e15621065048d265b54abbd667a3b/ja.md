```
getleft(Const(:something)) == :something
getleft(Identity(23))  # throws MethodError
```

"左側"の`Const`値から値を抽出します。他の何かに使用すると大きなエラーが発生します。
