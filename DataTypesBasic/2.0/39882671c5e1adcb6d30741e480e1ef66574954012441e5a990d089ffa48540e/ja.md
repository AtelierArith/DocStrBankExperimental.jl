```
getleftOption(Identity(23)) == Option()
getleftOption(Const(:something)) == Option(:something)
```

左の値を保持することを前提にオプションに変換します。
