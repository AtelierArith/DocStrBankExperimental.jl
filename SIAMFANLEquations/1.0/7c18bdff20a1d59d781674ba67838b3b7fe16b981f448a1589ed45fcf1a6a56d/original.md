secant(f,x0; rtol=1.e-6, atol=1.e-12, maxit=10,         armmax=10, armfix=false, pdata=nothing,         printerr=true, keepsolhist=true, stagnationok=false)

C. T. Kelley, 2022

The secant method for scalar equations. 

Input:

f: function

x0: initial iterate

Keyword Arguments (kwargs):

rtol, atol: real and absolute error tolerances

maxit: upper bound on number of nonlinear iterations

If you use secant and your initial iterate is poor, you have made a mistake. You will get an error message.

armmax: upper bound on stepsize reductions in linesearch

armfix:

The default is a parabolic line search (ie false). Set to true and the stepsize will be fixed at .5. Don't do this unless you are doing experiments for research.

printerr:

I print a helpful message when the solver fails. To suppress that message set printerr to false.

keepsolhist:

Set this to true to get the history of the iteration in the output tuple. This is on by default for scalar equations and off for systems. Only turn it on if you have use for the data, which can get REALLY LARGE.

stagnationok:

Set this to true if you want to disable the line search and either observe divergence or stagnation. This is only useful for research or writing a book.

Output:

A named tuple (solution, functionval, history, stats, idid,                errcode, solhist) where

solution = converged result functionval = F(solution) history = the vector of residual norms (||F(x)||) for the iteration stats = named tuple of the history of (ifun, ijac, iarm), the number of functions/derivatives/steplength reductions at each iteration. For the secant method, ijac = 0.

idid=true if the iteration succeeded and false if not.

errcode = 0 if if the iteration succeeded         = -1 if the initial iterate satisfies the termination criteria         = 10 if no convergence after maxit iterations         = 1  if the line search failed

solhist:

This is the entire history of the iteration if you've set keepsolhist=true

secant builds solhist with a function from the Tools directory. For systems, solhist is an N x K array where N is the length of x and K  is the number of iteration + 1. So, for scalar equations (N=1), solhist is a row vector. Hence the use of solhist' in the example below.

### Example for secant.jl

```jldoctest

julia> secout=secant(atan,1.0;maxit=6,atol=1.e-12,rtol=1.e-12);


julia> secout.history
7-element Array{Float64,1}:
 7.85398e-01
 5.18729e-01
 5.39030e-02
 4.86125e-03
 4.28860e-06
 3.37529e-11
 2.06924e-22
```
