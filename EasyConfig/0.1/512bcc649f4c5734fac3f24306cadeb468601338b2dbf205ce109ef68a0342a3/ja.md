```
Config(; kw...)
Config(::AbstractDict)
```

`OrderedDict{Symbol, Any}`のラッパーで、特別なプロパティを持っています：

1. `getproperty`/`setproperty!`を介してアイテムを取得/設定できます：

    c = Config()  c.one = 1  c.one == 1
2. 存在しないプロパティは自動的に作成されます：

    c = Config()  c.one.two.three = "neat!"
