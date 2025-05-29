```
getrightOption(Identity(23)) == Option(23)
getrightOption(Const(:something)) == Option()
```

オプションに変換します。右の値を保持したいと仮定します。`getOption`と同じですが、サイトについて明示的です。
