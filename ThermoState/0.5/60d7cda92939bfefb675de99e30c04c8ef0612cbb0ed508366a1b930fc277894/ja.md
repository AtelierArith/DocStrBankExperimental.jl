```
spec(sp::AbstractSpec,val,normalize_units=true)
spec(;kwargs,normalize_units=true)
```

仕様プロパティを生成します。キーワードインターフェースで呼び出すことができます：

```julia
sp = spec(t=32u"°C")
sp = spec(t=32u"°C",normalize_units = true)
```

または位置引数インターフェースで：

```julia
sp = spec(Types.Temperature(),32u"°C")
sp = spec(Types.Temperature(),32u"°C",true)
```

`normalize_units`がfalseに設定されている場合、単位付きの量はそのまま保存され、SI単位に変換されることはありません。

@spec_strマクロを使用して適切な`Spec`タイプを呼び出すことができます：

```julia
sp = spec(spec"t",32u"°C")
sp = spec(spec"t",32u"°C",true)
```
