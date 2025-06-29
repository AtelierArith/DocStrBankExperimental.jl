nsolsc(f,x0, fp=difffp; rtol=1.e-6, atol=1.e-12, maxit=10,         solver="newton", sham=1, armmax=10, resdec=.1, dx=1.e-7,         armfix=false, pdata=nothing,         printerr=true, keepsolhist=true, stagnationok=false)

C. T. Kelley, 2022

Newton's method for scalar equations. Has most of the features a code for systems of equations needs. This is a wrapper for a call to nsol.jl, the real code for systems. 

Input:

f: function

x0: initial iterate

fp: derivative. If your derivative function is fp, you give me its name. For example fp=foobar tells me that foobar is your function for the derivative. The default is a forward difference Jacobian that I provide.

Keyword Arguments (kwargs):

rtol, atol: real and absolute error tolerances

maxit: upper bound on number of nonlinear iterations

solver:

Your choices are "newton"(default) or "chord". However,  you have sham at your disposal only if you choose newton. "chord" will keep using the initial derivative until the iterate converges, uses the iteration budget, or the line search fails. It is not the same as sham=Inf, which is smarter.

If you use secant and your initial iterate is poor, you have made a mistake. I will help you by driving the line search with a finite difference derivative.

sham:

This is the Shamanskii method. If sham=1, you have Newton. The iteration updates the derivative every sham iterations. The convergence rate has local q-order sham+1 if you only count iterations where you update the derivative. You need not provide your own derivative function to use this option. sham=Inf is chord only if chord is converging well.

armmax: upper bound on stepsize reductions in linesearch

resdec: target value for residual reduction. 

The default value is .1. In the old MATLAB codes it was .5. I only turn Shamanskii on if the residuals are decreasing rapidly, at least a factor of resdec, and the line search is quiescent. If you want to eliminate resdec from the method ( you don't ) then set resdec = 1.0 and you will never hear from it again.  

dx:

This is the increment for forward difference, default = 1.e-7. dx should be roughly the square root of the noise in the function.

armfix:

The default is a parabolic line search (ie false). Set to true and the stepsize will be fixed at .5. Don't do this unless you are doing experiments for research.

pdata:

precomputed data for the function/derivative. Things will go better if you use this rather than hide the data in global variables within the module for your function/derivative If you use this option your function and derivative must take pdata as a second argument. eg f(x,pdata) and fp(x,pdata)

printerr:

I print a helpful message when the solver fails. To suppress that message set printerr to false.

keepsolhist:

Set this to true to get the history of the iteration in the output tuple. This is on by default for scalar equations and off for systems. Only turn it on if you have use for the data, which can get REALLY LARGE.

stagnationok:

Set this to true if you want to disable the line search and either observe divergence or stagnation. This is only useful for research or writing a book.

Output:

A named tuple (solution, functionval, history, stats, idid,                errcode, solhist) where

solution = converged result functionval = F(solution) history = the vector of residual norms (||F(x)||) for the iteration stats = named tuple of the history of (ifun, ijac, iarm), the number of functions/derivatives/steplength reductions at each iteration.

I do not count the function values for a finite-difference derivative because they count toward a Jacobian evaluation. I do count them for the secant method model.

idid=true if the iteration succeeded and false if not.

errcode = 0 if if the iteration succeeded         = -1 if the initial iterate satisfies the termination criteria         = 10 if no convergence after maxit iterations         = 1  if the line search failed

solhist:

This is the entire history of the iteration if you've set keepsolhist=true

nsolsc builds solhist with a function from the Tools directory. For systems, solhist is an N x K array where N is the length of x and K  is the number of iteration + 1. So, for scalar equations (N=1), solhist is a row vector. Hence the use of solhist' in the example below.

### Examples for nsolsc.jl

```jldoctest
julia> nsolout=nsolsc(atan,1.0;maxit=5,atol=1.e-12,rtol=1.e-12);

julia> nsolout.history
6-element Array{Float64,1}:
 7.85398e-01
 5.18669e-01
 1.16332e-01
 1.06102e-03
 7.96200e-10
 2.79173e-24
```

# If you have an analytic derivative, I will use it.

```jldoctest
julia> fs(x)=x^2-4.0; fsp(x)=2x;

julia> nsolout=nsolsc(fs,1.0,fsp; maxit=5,atol=1.e-9,rtol=1.e-9);

julia> [nsolout.solhist'.-2 nsolout.history]
6×2 Array{Float64,2}:
 -1.00000e+00  3.00000e+00
  5.00000e-01  2.25000e+00
  5.00000e-02  2.02500e-01
  6.09756e-04  2.43940e-03
  9.29223e-08  3.71689e-07
  2.22045e-15  8.88178e-15

```

# You can also use anonymous functions

```jldoctest
julia> nsolout=nsolsc(atan,10.0,x -> 1.0/(1.0+x^2); 
atol=1.e-9,rtol=1.e-9);

julia> nsolout.history
8-element Vector{Float64}:
 1.47113e+00
 1.19982e+00
 1.10593e+00
 6.48297e-01
 2.56983e-01
 1.19361e-02
 1.13383e-06
 9.71970e-19
```
