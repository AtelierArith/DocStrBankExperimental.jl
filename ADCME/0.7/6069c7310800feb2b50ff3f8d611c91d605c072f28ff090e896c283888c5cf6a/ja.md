```
CustomOptimizer(opt::Function, name::String)
```

は、構造体名 `name` のカスタムオプティマイザを作成します。例えば、`Optim.jl` を `ADCME` と統合するために、新しいオプティマイザを構築することができます。

```julia
CustomOptimizer("Con") do f, df, c, dc, x0, x_L, x_U
    opt = Opt(:LD_MMA, length(x0))
    bd = zeros(length(x0)); bd[end-1:end] = [-Inf, 0.0]
    opt.lower_bounds = bd
    opt.xtol_rel = 1e-4
    opt.min_objective = (x,g)->(g[:]= df(x); return f(x)[1])
    inequality_constraint!(opt, (x,g)->( g[:]= dc(x);c(x)[1]), 1e-8)
    (minf,minx,ret) = NLopt.optimize(opt, x0)
    minx
end
```

ここで

∘ `f`: $f(x)$ を返す関数

∘ `df`: $\nabla f(x)$ を返す関数

∘ `c`: 制約 $c(x)$ を返す関数

∘ `dc`: $\nabla c(x)$ を返す関数

∘ `x0`: 初期推定値

∘ `nineq`: 不等式制約の数

∘ `neq`: 等式制約の数

∘ `x_L`: 最適化可能な変数の下限

∘ `x_U`: 最適化可能な変数の上限

次に、以下のようにオプティマイザを作成できます。

```
opt = Con(loss, inequalities=[c1], equalities=[c2])
```

最適化をトリガーするには、次のようにします。

```
minimize(opt, sess)
```

Juliaのグローバル変数スコープのおかげで、`step_callback`、`optimizer_kwargs` は実際にJulia環境から直接渡すことができます。
