```
argsdict([args_list::Vector];
         first_arg::Int = 1,
         delim = '=',
         as_symbols::Bool = false,
         default_named_type::Type = ITensors.AutoType,
         save_positional::Bool = true,
         default_positional_type::Type = String,
         prefix::String = "_arg")
```

コマンドライン引数を解析します。例えば `julia N=2 X=1e-12` のように、辞書に格納します。キーは区切り文字の前、値は後ろに配置され、結果は `Dict("N" => "2", "X" => "1e-12")` となります。
