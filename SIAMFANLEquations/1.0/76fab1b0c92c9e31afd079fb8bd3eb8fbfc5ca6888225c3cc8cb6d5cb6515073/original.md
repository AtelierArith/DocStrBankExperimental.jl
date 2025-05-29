```
nsol(F!, x0, FS, FPS, J!=diffjac!; rtol=1.e-6, atol=1.e-12,
           maxit=20, solver="newton", sham=5, armmax=10, resdec=.1,
           dx = 1.e-7, armfix=false, 
           pdata = nothing, jfact = klfact,
           printerr = true, keepsolhist = false, stagnationok=false)
```

C. T. Kelley, 2022

Julia versions of the nonlinear solvers from my SIAM books.  Herewith: nsol

You must allocate storage for the function and Jacobian in advance –> in the calling program <– ie. in FS and FPS

Inputs:

  * F!: function evaluation, the ! indicates that F! overwrites FS, your   preallocated storage for the function.

    So FS=F!(FS,x) or FS=F!(FS,x,pdata) returns FS=F(x)

    Your function MUST have –> return FS <– at the end.   See the examples in the docstrings and in TestProblems/Systems/simple.jl
  * x0: initial iterate

  * FS: Preallocated storage for function. It is a vector of size N

    You should store it as (N) and design F! to use vectors of size (N).  If you use (N,1) consistently instead, the solvers may work, but I make no guarantees.
  * FPS: preallocated storage for Jacobian. It is an N x N matrix

  * J!: Jacobian evaluation, the ! indicates that J! overwrites FPS, your   preallocated storage for the Jacobian. If you leave this out the   default is a finite difference Jacobian.

    So, FP=J!(FP,FS,x) or FP=J!(FP,FS,x,pdata) returns FP=F'(x). 

    (FP,FS, x) must be the argument list, even if FP does not need FS.   One reason for this is that the finite-difference Jacobian   does and that is the default in the solver.

    Your Jacobian function MUST have –> return FP <– at the end.   See the examples in the docstrings and in TestProblems/Systems/simple.jl

  * Precision: Lemme tell ya 'bout precision. I designed this code for    full precision functions and linear algebra in any precision you want.    You can declare   FPS as Float64, Float32, or Float16 and nsol will do the right thing if   YOU do not destroy the declaration in your J! function. I'm amazed   that this works so easily. If the Jacobian is reasonably well    conditioned, you can cut the cost of Jacobian factorization and   storage in half with no loss. For large dense Jacobians and inexpensive   functions, this is a good deal.

    BUT ... There is very limited support for direct sparse solvers in   anything other than Float64. I recommend that you only use Float64   with direct sparse solvers unless you really know what you're doing. I   have a couple examples in the notebook, but watch out.

---

Keyword Arguments (kwargs):

rtol and atol: relative and absolute error tolerances

maxit: limit on nonlinear iterations

solver: default = "newton"

Your choices are "newton" or "chord". However, you have sham at your disposal only if you chose newton. "chord" will keep using the initial derivative until the iterate converges, uses the iteration budget, or the line search fails. It is not the same as sham=Inf, which is smarter.

sham: default = 5 (ie Newton)

This is the Shamanskii method. If sham=1, you have Newton. The iteration updates the derivative every sham iterations. The convergence rate has local q-order sham+1 if you only count iterations where you update the derivative. You need not provide your own derivative function to use this option. sham=Inf is chord only if chord is converging well.

I made sham=1 the default for scalar equations. For systems I'm more aggressive and want to invest as little energy in linear algebra as possible. So the default is sham=5.

armmax: upper bound on step size reductions in line search

resdec: default = .1

This is the target value for residual reduction. The default value is .1. In the old MATLAB codes it was .5. I only turn Shamanskii on if the residuals are decreasing rapidly, at least a factor of resdec, and the line search is quiescent. If you want to eliminate resdec from the method ( you don't ) then set resdec = 1.0 and you will never hear from it again.

dx: default = 1.e-7

difference increment in finite-difference derivatives       h=dx*norm(x,Inf)+1.e-8

armfix: default = false

The default is a parabolic line search (ie false). Set to true and the step size will be fixed at .5. Don't do this unless you are doing experiments for research.

pdata:

precomputed data for the function/Jacobian.  Things will go better if you use this rather than hide the data  in global variables within the module for your function/Jacobian

If you use pdata in either of F! or J!, you must use in in the  calling sequence of both.

jfact: default = klfact (tries to figure out best choice) 

If your Jacobian has any special structure, please set jfact to the correct choice for a factorization.

I use jfact when I call PrepareJac! to evaluate the Jacobian (using your J!) and factor it. The default is to use klfact (an internal function) to do something reasonable. For general dense matrices, klfact picks lu! to compute an LU factorization and share storage with the Jacobian.  You may change LU to something else by, for example, setting jfact = cholesky! if your Jacobian is spd.

klfact knows about banded matrices and picks qr. You should, however RTFM, allocate the extra two upper bands, and use jfact=qr! to override klfact.

klfact uses lu for general sparse matrices.

If you give me something that klfact does not know how to dispatch on, then nothing happens. I just return the original Jacobian matrix and  nsol will use backslash to compute the Newton step. I know that this is probably not optimal in your situation, so it is  good to pick something else, like jfact = lu.

If you want to manage your own factorization within your Jacobian  evaluation function, then set

jfact = nofact

and nsol will not attempt to factor your Jacobian. That is also what happens when klfact does not know what to do. Your Jacobian is sent directly to Julia's \  operation

Please do not mess with the line that calls PrepareJac!. 

```
    FPF = PrepareJac!(FPS, FS, x, ItRules)
```

FPF is not the same as FPS (the storage you allocate for the Jacobian) for a reason. FPF and FPS do not have the same type, even though they share storage. So, FPS=PrepareJac!(FPS, FS, ...) will break things.

printerr: default = true

I print a helpful message when the solver fails. To suppress that message set printerr to false.

keepsolhist: default = false

Set this to true to get the history of the iteration in the output tuple. This is on by default for scalar equations and off for systems. Only turn it on if you have use for the data, which can get REALLY LARGE.

stagnationok: default = false

Set this to true if you want to disable the line search and either observe divergence or stagnation. This is only useful for research or writing a book.

Output:

  * A named tuple (solution, functionval, history, stats, idid,              errcode, solhist)

where

– solution = converged result

– functionval = F(solution)

– history = the vector of residual norms (||F(x)||) for the iteration

– stats = named tuple of the history of (ifun, ijac, iarm), the number of functions/derivatives/steplength reductions at each iteration.

I do not count the function values for a finite-difference derivative because they count toward a Jacobian evaluation. 

– idid=true if the iteration succeeded and false if not.

– errcode = 0 if the iteration succeeded

```
    = -1 if the initial iterate satisfies the termination criteria

    = 10 if no convergence after maxit iterations

    = 1  if the line search failed
```

– solhist:

This is the entire history of the iteration if you've set keepsolhist=true

solhist is an N x K array where N is the length of x and K is the number of iterations + 1. So, for scalar equations, it's a row vector.

---

### Examples for nsol

#### World's easiest problem example.

Test 64 and 32 bit Jacobians. No meaningful difference in the residual histories or the converged solutions.

```jldoctest
 julia> function f!(fv,x)
       fv[1]=x[1] + sin(x[2])
       fv[2]=cos(x[1]+x[2])
#
# The return fv part is important even though f! overwrites fv.
#
       return fv
       end
f (generic function with 1 method)

julia> x=ones(2); fv=zeros(2); jv=zeros(2,2); jv32=zeros(Float32,2,2);
julia> nout=nsol(f!,x,fv,jv; sham=1);
julia> nout32=nsol(f!,x,fv,jv32; sham=1);
julia> [nout.history nout32.history]
5×2 Matrix{Float64}:
 1.88791e+00  1.88791e+00
 2.43119e-01  2.43120e-01
 1.19231e-02  1.19231e-02
 1.03266e-05  1.03265e-05
 1.46388e-11  1.45995e-11

julia> [nout.solution nout.solution-nout32.solution]
2×2 Array{Float64,2}:
 -7.39085e-01  -5.48450e-14
  2.30988e+00  -2.26485e-14
```

#### H-equation example.

I'm taking the sham=5 default here, so the convergence is not quadratic. The good news is that we evaluate the Jacobian only once.

```jldoctest
julia> n=16; x0=ones(n); FV=ones(n); JV=ones(n,n);
julia> hdata=heqinit(x0, .5);
julia> hout=nsol(heqf!,x0,FV,JV;pdata=hdata);
julia> hout.history
4-element Array{Float64,1}:
 6.17376e-01
 3.17810e-03
 2.75227e-05
 2.35817e-07
```
