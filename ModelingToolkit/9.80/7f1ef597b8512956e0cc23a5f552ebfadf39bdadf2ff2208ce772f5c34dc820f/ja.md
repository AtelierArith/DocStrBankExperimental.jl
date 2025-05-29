```
debug_system(sys::AbstractSystem; functions = [log, sqrt, (^), /, inv, asin, acos], error_nonfinite = true)
```

`functions`を`sys`でラップして、これらの中で発生したエラーが入力に関する有用な記号的数値情報を表示するようにします。`error_nonfinite`が`true`の場合、非有限値（例えば`Inf`や`NaN`）を出力する関数は、原始的な関数自体が例外をスローしない場合（例えば`1/0`のように）でもエラーを表示します。例えば：

```julia-repl
julia> sys = debug_system(complete(sys))

julia> prob = ODEProblem(sys, [0.0, 2.0], (0.0, 1.0))

julia> prob.f(prob.u0, prob.p, 0.0)
ERROR: Function /(1, sin(P(t))) output non-finite value Inf with input
  1 => 1
  sin(P(t)) => 0.0
```

さらに、システム内のすべてのアサーションは、失敗したときにオプションでログに記録されます。アサーションが失敗したときに関連するメッセージがログに記録されるかどうかを制御する新しいパラメータもシステムに追加されます。このパラメータはデフォルトで`true`であり、`ModelingToolkit.ASSERTION_LOG_VARIABLE`を使ったシンボリックインデックスで切り替えることができます。例えば、`prob.ps[ModelingToolkit.ASSERTION_LOG_VARIABLE] = false`はログ記録を無効にします。
