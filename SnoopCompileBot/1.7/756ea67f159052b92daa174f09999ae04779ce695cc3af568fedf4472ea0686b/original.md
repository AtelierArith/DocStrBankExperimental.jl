```
@snoopi_bench botconfig::BotConfig, snoop_script::Expr
```

!!! warning
    This method isn't recommend. Use `snoopi_bench(config::BotConfig, path_to_example_script::String)` instead.


# Examples

Benchmarking the load infer time

```julia
using SnoopCompile

println("loading infer benchmark")
@snoopi_bench BotConfig("MatLang") begin
 using MatLang
end
```

Benchmarking the example infer time

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
