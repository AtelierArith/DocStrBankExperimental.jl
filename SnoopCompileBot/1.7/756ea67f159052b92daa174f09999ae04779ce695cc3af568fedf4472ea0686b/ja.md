```
@snoopi_bench botconfig::BotConfig, snoop_script::Expr
```

!!! warning
    このメソッドは推奨されていません。代わりに `snoopi_bench(config::BotConfig, path_to_example_script::String)` を使用してください。


# 例

ロード推論時間のベンチマーク

```julia
using SnoopCompile

println("loading infer benchmark")
@snoopi_bench BotConfig("MatLang") begin
 using MatLang
end
```

例の推論時間のベンチマーク

```julia
SnoopCompile

println("examples infer benchmark")
@snoopi_bench BotConfig("MatLang") begin
    using MatLang
    MatLang_rootpath = dirname(dirname(pathof("MatLang")))

    include("$MatLang_rootpath/examples/Language_Fundamentals/usage_Matrices_and_Arrays.jl")
    include("$MatLang_rootpath/examples/Language_Fundamentals/Data_Types/usage_Numeric_Types.jl")
end
```
