```
setvalueanddefault!(par::Parameter, value; freeze=false)
```

パラメータの値を設定し、デフォルトを `value` に設定します。

オプションとして（[`Parameter`](@ref) が Type パラメータ `ParseFromString != Nothing` を持つ場合）、`value` を文字列から解析します。
