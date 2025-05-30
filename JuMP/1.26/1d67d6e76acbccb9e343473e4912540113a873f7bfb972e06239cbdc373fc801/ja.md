```
solution_summary(model::GenericModel; result::Int = 1, verbose::Bool = false)
```

結果 `result` の解の要約を印刷するために使用できる構造体を返します。

`verbose=true` の場合、空の名前を持つものを除いて、すべての変数の原始解とすべての制約の双対解を出力します。

## 例

REPL で呼び出されると、要約が自動的に印刷されます：

```jldoctest
julia> model = Model();

julia> solution_summary(model)
solution_summary(; result = 1, verbose = false)
├ solver_name          : No optimizer attached.
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION
```

関数内から要約の印刷を強制するには `print` を使用します：

```jldoctest
julia> model = Model();

julia> function foo(model)
           print(solution_summary(model))
           return
       end
foo (generic function with 1 method)

julia> foo(model)
solution_summary(; result = 1, verbose = false)
├ solver_name          : No optimizer attached.
├ Termination
│ ├ termination_status : OPTIMIZE_NOT_CALLED
│ ├ result_count       : 0
│ └ raw_status         : optimize not called
└ Solution (result = 1)
  ├ primal_status        : NO_SOLUTION
  └ dual_status          : NO_SOLUTION
```
