```
CustomOptimizer(opt::Function, name::String)
```

creates a custom optimizer with struct name `name`. For example, we can integrate `Optim.jl` with `ADCME` by  constructing a new optimizer

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

Here

∘ `f`: a function that returns $f(x)$

∘ `df`: a function that returns $\nabla f(x)$

∘ `c`: a function that returns the constraints $c(x)$

∘ `dc`: a function that returns $\nabla c(x)$

∘ `x0`: initial guess

∘ `nineq`: number of inequality constraints

∘ `neq`: number of equality constraints

∘ `x_L`: lower bounds of optimizable variables

∘ `x_U`: upper bounds of optimizable variables

Then we can create an optimizer with 

```
opt = Con(loss, inequalities=[c1], equalities=[c2])
```

To trigger the optimization, use

```
minimize(opt, sess)
```

Note thanks to the global variable scope of Julia, `step_callback`, `optimizer_kwargs` can actually  be passed from Julia environment directly.
