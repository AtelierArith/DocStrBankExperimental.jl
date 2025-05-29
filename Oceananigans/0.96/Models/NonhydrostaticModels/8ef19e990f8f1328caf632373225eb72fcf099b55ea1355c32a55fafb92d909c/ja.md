```
BackgroundField(func; parameters=nothing)
```

`NonhydrostaticModel`に渡され、背景速度またはトレーサーフィールドとして使用される`BackgroundField`を返します。

`parameters`が提供されていない場合、`func`は次のシグネチャで呼び出し可能でなければなりません。

```julia
func(x, y, z, t)
```

`parameters`が提供されている場合、`func`は次のシグネチャで呼び出し可能でなければなりません。

```julia
func(x, y, z, t, parameters)
```
