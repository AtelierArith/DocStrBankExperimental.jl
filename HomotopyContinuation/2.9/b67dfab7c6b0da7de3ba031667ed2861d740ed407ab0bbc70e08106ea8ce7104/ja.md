```
verify_solution_completeness(F::System, monodromy_result; options...)
verify_solution_completeness(F::System, solutions, parameters;
    trace_tol = 1e-14,
    show_progress = true,
    compile = COMPILE_DEFAULT[],
    monodromy_options = (compile = compile,),
    parameter_homotopy_options = (compile = compile,),
)
```

[`monodromy_solve`](@ref)によってモノドロミー計算がすべての解を見つけたことを確認します。これは、[^\dCR17]および[^\LRS18]で説明されているトレーステストを使用します。トレースは数値であり、すべての解が見つかった場合は0になります。このために`trace_tol`キーワード引数が使用されます。関数は、いくつかの計算が実行できなかった場合は`nothing`を返します。それ以外の場合はブール値を返します。この関数は、モノドロミーを使用して別の多項式系の解を計算することを必要とします。このルーチンは、追加の解のセットが完全でない場合、すべての解が見つかっていても`false`を返すことがあります。

### 例

```julia
@var x y a b c;
f = x^2+y^2-1;
l = a*x+b*y+c;
sys = System([f, l]; parameters = [a, b, c]);
mres = monodromy_solve(sys, [-0.6-0.8im, -1.2+0.4im], [1,2,3]);
show(mres);
verify_solution_completeness(sys, mres)
```

```
MonodromyResult
==================================
• 2 solutions (0 real)
• return code → heuristic_stop
• 44 tracked paths
• seed → 367230
julia> verify_solution_completeness(sys, mres)
[ Info: 提供された解を認証しています...
[ Info: 2つの異なる解を取得しました。
[ Info: 完全性のために追加の証人を計算しています...
┌ Info: MonodromyResult
│ ===============
│ • return_code → :heuristic_stop
│ • 4 solutions
│ • 28 tracked loops
└ • random_seed → 0x21e7406a
[ Info: 追加の証人を認証しています...
[ Info: 2つの追加の証人を計算しました
[ Info: 2つのパラメーターホモトピーを使用してトレースを計算しています...
[ Info: トレースのノルム: 9.33238819760471e-17
true
```

[^dCR17]: del Campo, Abraham Martín, and Jose Israel Rodriguez. "Critical points via monodromy and local methods." Journal of Symbolic Computation 79 (2017): 559-574.

[^LRS18]: Leykin, Anton, Jose Israel Rodriguez, and Frank Sottile. "Trace test." Arnold Mathematical Journal 4.1 (2018): 113-125.
