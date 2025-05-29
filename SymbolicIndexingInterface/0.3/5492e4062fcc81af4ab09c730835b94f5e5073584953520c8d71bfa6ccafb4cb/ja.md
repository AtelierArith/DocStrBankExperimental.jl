```
timeseries_parameter_index(indp, sym)
```

`sym`の`indp`における時系列パラメータのインデックスを返します。このインデックスは[`ParameterTimeseriesIndex`](@ref)オブジェクトとして返されます。`sym`が`indp`の時系列パラメータでない場合は`nothing`を返します。デフォルトでは`nothing`を返します。`indp`に`symbolic_container`が存在する場合は、それを考慮します。
