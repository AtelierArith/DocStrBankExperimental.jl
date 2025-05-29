```
get_param_index(param::AbstractString)
```

パラメータ "T"、"P" などのインデックスを長整数として取得します。これは `abstractstate_keyed_output()` 関数用です。

# 引数

  * `param`: パラメータ名を表す文字列。完全なリストを確認するには「PropsSI 関数への文字列入力の表」を参照してください: http://www.coolprop.org/coolprop/HighLevelAPI.html#parameter-table、または単に `get_global_param_string("parameter_list")` と入力してください。
