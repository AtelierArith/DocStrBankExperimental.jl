```
ParameterProcess(variable, value = default_value(variable)) <: Process
```

与えられた `variable` を定数値に等しくする最も単純なプロセスであり、その値はパラメータにカプセル化されています。もし `value isa Real` であれば、`variable` の名前と `_0` を付加した名前のパラメータが作成されます。そうでなければ、`value isa Num` の場合は、それがパラメータとして直接使用されます。

例:

```julia
@variables T(t) = 0.5
proc = ParameterProcess(T)
```

は、`T ~ T_0` という方程式を作成します。ここで `T_0` はデフォルト値 `0.5` を持つ `@parameter` です。
