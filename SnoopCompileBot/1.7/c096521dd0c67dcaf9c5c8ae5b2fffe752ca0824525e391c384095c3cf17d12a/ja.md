```
@snoopi_bot config::BotConfig  snoop_script::Expr
@snoopi_bot config::BotConfig
```

!!! warning
    このマクロは推奨されていません。代わりに関数形式を使用してください: `snoopi_bot(config::BotConfig, path_to_example_script::String)`.


# 例

```julia
using SnoopCompile


@snoopi_bot BotConfig("MatLang") begin
  using MatLang
  MatLang_rootpath = dirname(dirname(pathof("MatLang")))

  include("$MatLang_rootpath/examples/Language_Fundamentals/usage_Matrices_and_Arrays.jl")
  include("$MatLang_rootpath/examples/Language_Fundamentals/Data_Types/usage_Numeric_Types.jl")
end
```
