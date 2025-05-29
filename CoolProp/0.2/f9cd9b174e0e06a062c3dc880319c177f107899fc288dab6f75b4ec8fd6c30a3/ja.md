```
get_parameter_information_string(key::AbstractString, outtype::AbstractString)
get_parameter_information_string(key::AbstractString)
```

パラメータの情報を取得します。

# 引数

  * `key`: パラメータ名を表す文字列。完全なリストを確認するには「PropsSI関数への文字列入力の表」を参照してください: http://www.coolprop.org/coolprop/HighLevelAPI.html#parameter-table、または単に `get_global_param_string("parameter_list")` と入力してください。
  * `outtype="long"`: 出力タイプ。`["IO", "short", "long", "units"]` のいずれかで、デフォルト値は "long" です。

# 例

```julia
julia> get_parameter_information_string("HMOLAR")
"Molar specific enthalpy"
julia> get_parameter_information_string("HMOLAR", "units")
"J/mol"
```

# 注意

この関数の表形式の出力は `?CoolProp_parameters` で利用可能です。
