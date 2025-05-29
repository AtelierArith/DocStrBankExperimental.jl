```
setvalue!(par::Parameter, value)
```

パラメータを `value` に設定します。

オプションで（[`Parameter`](@ref) が Type パラメータ `ParseFromString != Nothing` を持つ場合）、`value` を文字列から解析します。
