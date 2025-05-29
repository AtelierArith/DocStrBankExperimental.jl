```
OptimOptionsθ(; 
f_tol = 1.0e-8, 
g_tol = 1.0e-4, 
x_tol = 1.0e-5, 
iterations = 25, 
show_trace = true, 
store_trace = true, 
extended_trace = true )
```

Creates and returns an *OptimOptions* optimization options variable for the outer optimization algorithm, including the function value tolerance, the gradient tolerance, the solution tolerance, the maximum number of iterations, whether to show the trace, whether to store the trace, and whether to keep the extended trace.  See the **Optim** package for details.  

The current version of Grumps will largely ignore the trace-related parameters.
