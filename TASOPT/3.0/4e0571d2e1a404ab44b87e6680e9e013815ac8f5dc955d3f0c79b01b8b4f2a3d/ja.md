```
generate_par_indname(par_suffix::AbstractVector{String}=["i","g","m","a","e"])
```

文字列の接尾辞のベクトルを与えると、各接尾辞に対して `generate_par_indname(par_suffix::String)` を呼び出し、キー `"par"*par_suffix` を持つ `Dict` に保存し、その `Dict` を返します。デフォルトでは、デフォルトモデルの par_arrays に設定されています。
