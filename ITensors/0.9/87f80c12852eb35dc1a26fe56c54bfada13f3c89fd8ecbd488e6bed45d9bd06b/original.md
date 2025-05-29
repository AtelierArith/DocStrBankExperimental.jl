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

Parse the command line arguments such as `julia N=2 X=1e-12` and put them in a dictionary, where the keys are before the delimiter and the values are after, so `Dict("N" => "2", "X" => "1e-12")`.
