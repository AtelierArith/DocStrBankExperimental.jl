```
getOption(Identity(23)) == Option(23)
getOption(Const(:something)) == Option()
```

オプションに変換します。右側の値が保持され、左側の値が `Option()` として表されると仮定します。
