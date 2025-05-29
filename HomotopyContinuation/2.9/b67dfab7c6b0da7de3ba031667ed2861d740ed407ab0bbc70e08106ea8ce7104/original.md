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

Verify that a monodromy computation found all solutions by [`monodromy_solve`](@ref). This uses the trace test described in [^dCR17] and [^LRS18]. The trace is a numerical value which is 0 if all solutions are found, for this the `trace_tol` keyword argument is used. The function returns `nothing` if some computation couldn't be carried out. Otherwise returns a boolean. Note that this function requires the computation of solutions to another polynomial system using monodromy. This routine can return `false` although all solutions are found if this additional solution set is not complete.

### Example

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
[ Info: Certify provided solutions...
[ Info: Got 2 dinstinct solutions.
[ Info: Compute additional witnesses for completeness...
┌ Info: MonodromyResult
│ ===============
│ • return_code → :heuristic_stop
│ • 4 solutions
│ • 28 tracked loops
└ • random_seed → 0x21e7406a
[ Info: Certify additional witnesses...
[ Info: Computed 2 additional witnesses
[ Info: Compute trace using two parameter homotopies...
[ Info: Norm of trace: 9.33238819760471e-17
true
```

[^dCR17]: del Campo, Abraham Martín, and Jose Israel Rodriguez. "Critical points via monodromy and local methods." Journal of Symbolic Computation 79 (2017): 559-574.

[^LRS18]: Leykin, Anton, Jose Israel Rodriguez, and Frank Sottile. "Trace test." Arnold Mathematical Journal 4.1 (2018): 113-125.
