```
print_macro_timing_summary([io::IO = stdout], model::GenericModel)
```

各マクロの実行時間の概要を表示します。

このメソッドを呼び出す前に、[`set_macro_timing`](@ref)を使用してマクロタイミング機能を有効にする必要があります。

## 例

```jldoctest; filter=[r"Total time inside macros: .+ seconds", r"├.+", r"└.+"]
julia> begin
           model = Model()
           set_macro_timing(model, true)
           @variable(model, x[1:2])
           @objective(model, Min, sum(x))
       end;

julia> print_macro_timing_summary(model)
Total time inside macros: 5.33690e-02 seconds
│
├ 2.96490e-02 s [55.55%]
│ ├ REPL[8]:3
│ └ `@variable(model, x[1:2])`
│
└ 2.37200e-02 s [44.45%]
  ├ REPL[8]:4
  └ `@objective(model, Min, sum(x))`
```
