デフォルト値を持つ設定可能なオプション（値0およびNaNは無制限を示します）：

```
x_abstol::Real = -Inf,
x_reltol::Real = 2eps(),
f_abstol::Real = 1e-50,
f_reltol::Real = 2eps(),
f_mindec::Real = 1e-4,
g_restol::Real = sqrt(eps()),
x_abstol_break::Real = Inf,
x_reltol_break::Real = Inf,
f_abstol_break::Real = Inf,
f_reltol_break::Real = Inf,
g_restol_break::Real = Inf,
f_calls_limit::Int = 0,
g_calls_limit::Int = 0,
h_calls_limit::Int = 0,
allow_f_increases::Bool = true,
min_iterations::Int = 0,
max_iterations::Int = 1_000,
warn_iterations::Int = max_iterations,
show_trace::Bool = false,
store_trace::Bool = false,
extended_trace::Bool = false,
show_every::Int = 1,
verbosity::Int = 1
```
