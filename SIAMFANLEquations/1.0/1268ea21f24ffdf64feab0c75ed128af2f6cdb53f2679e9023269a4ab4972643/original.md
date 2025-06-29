ptcsol(F!, x0, FS, FPS, J! = diffjac!; rtol=1.e-6, atol=1.e-12,              maxit=20, delta0=1.e-6, dx=1.e-7, pdata = nothing, jfact = klfact,                printerr = true, keepsolhist = false, jknowsdt = false)

C. T. Kelley, 2022

Julia versions of the nonlinear solvers from my SIAM books.  Herewith: some new stuff ==> ptcsol

PTC finds the steady-state solution of u' = -F(u), u(0) = u_0. The - sign is a convention.

You must allocate storage for the function and Jacobian in advance –> in the calling program <– ie. in FS and FPS

Inputs:

  * F!: function evaluation, the ! indicates that F! overwrites FS, your   preallocated storage for the function.

    So, FS=F!(FS,x) or FS=F!(FS,x,pdata) returns FS=F(x)

    Your function MUST have –> return FS <– at the end.   See the examples in the TestProblems/Systems/FBeam!.jl
  * x0: initial iterate

  * FS: Preallocated storage for function. It is a vector of size N

    You should store it as (N) and design F! to use vectors of size (N). If you use (N,1) consistently instead, the solvers may work, but I make no guarantees.
  * FPS: preallocated storage for Jacobian. It is an N x N matrix

    If FPS is sparse, you **must** allocate storage for the diagonal so I will have room to put 1/dt in there.
  * J!: Jacobian evaluation, the ! indicates that J! overwrites FPS, your   preallocated storage for the Jacobian. If you leave this out the   default is a finite difference Jacobian.

    So, FP=J!(FP,FS,x) or FP=J!(FP,FS,x,pdata) returns FP=F'(x);   (FP,FS, x) must be the argument list, even if FP does not need FS.   One reason for this is that the finite-difference Jacobian   does and that is the default in the solver.

    Your Jacobian function MUST have –> return FP <– at the end.    See the examples in the TestProblems/Systems/FBeam!.jl

    You may have a better way to add (1/dt) I to your Jacobian. If you   want to do this yourself then your Jacobian function should be   FP=J!(FP,FS,x,dt) or FP=J!(FP,FS,x,dt,pdata) and return   F'(x) + (1.0/dt)*I. 

    You will also have to set the kwarg **jknowsdt** to true.
  * Precision: Lemme tell ya 'bout precision. I designed this code for    full precision   functions and linear algebra in any precision you want. You can declare   FPS as Float64, Float32, or Float16 and ptcsol will do the right thing if   YOU do not destroy the declaration in your J! function. I'm amazed   that this works so easily. If the Jacobian is reasonably well   conditioned, you can cut the cost of Jacobian factorization and   storage in half with no loss. For large dense Jacobians and inexpensive   functions, this is a good deal.

    BUT ... There is very limited support for direct sparse solvers in   anything other than Float64. I recommend that you only use Float64   with direct sparse solvers unless you really know what you're doing. I   have a couple examples in the notebook, but watch out.

---

Keyword Arguments (kwargs):

rtol and atol: relative and absolute error tolerances

delta0: initial pseudo time step. The default value of 1.e-3 is a bit conservative and is one option you really should play with. Look at the example where I set it to 1.0!

maxit: limit on nonlinear iterations, default=100. 

This is coupled to delta0. If your choice of delta0 is too small (conservative) then you'll need many iterations to converge and will need a larger value of maxit

For PTC you'll need more iterations than for a straight-up nonlinear solve. This is part of the price for finding the  stable solution.

dx: default = 1.e-7

difference increment in finite-difference derivatives       h=dx*norm(x)+1.e-6

pdata:

precomputed data for the function/Jacobian.  Things will go better if you use this rather than hide the data  in global variables within the module for your function/Jacobian

jfact: default = klfact (tries to figure out best choice) 

If your Jacobian has any special structure, please set jfact to the correct choice for a factorization.

I use jfact when I call PTCUpdate to evaluate the Jacobian (using your J!) and factor it. The default is to use klfact (an internal function) to do something reasonable. For general dense matrices, klfact picks lu! to compute an LU factorization and share storage with the Jacobian.  You may change LU to something else by, for example, setting jfact = cholseky! if your Jacobian is spd.

klfact knows about banded matrices and picks qr. You should, however RTFM, allocate the extra two upper bands, and use jfact=qr! to override klfact.

klfact uses lu for general sparse matrices.

If you give me something that klfact does not know how to dispatch on, then nothing happens. I just return the original Jacobian matrix and  ptcsol will use backslash to compute the Newton step.

I know that this is probably not optimal in your situation, so it is  good to pick something else, like jfact = lu.

printerr: default = true

I print a helpful message when the solver fails. To suppress that message set printerr to false.

keepsolhist: default = false

Set this to true to get the history of the iteration in the output tuple. This is on by default for scalar equations and off for systems. Only turn it on if you have use for the data, which can get REALLY LARGE.

jknowsdt: default = false

Set this to true if your Jacobian evaluation function returns F'(x) + (1/dt) I. You'll also need to follow the rules above for the Jacobian evaluation function. I do not recommend this and if your Jacobian is anything other than a matrix I can't promise anything. I've tested this for matrix outputs only.

Output:

A named tuple (solution, functionval, history, stats, idid,                errcode, solhist) where

solution = converged result functionval = F(solution) history = the vector of residual norms (||F(x)||) for the iteration

Unlike nsol, nsoli, or even ptcsoli, ptcsol has a fixed cost per  iteration of one function, one Jacobian, and one Factorization. Hence iteration statistics are not interesting and not in the output. 

idid=true if the iteration succeeded and false if not.

errcode = 0 if the iteration succeeded         = -1 if the initial iterate satisfies the termination criteria         = 10 if no convergence after maxit iterations

solhist:

This is the entire history of the iteration if you've set keepsolhist=true

solhist is an N x K array where N is the length of x and K is the number of iteration + 1. So, for scalar equations, it's a row vector.

### Example for ptcsol

#### The buckling beam problem.

You'll need to use TestProblems for this to work.

```jldoctest
julia> using SIAMFANLEquations.TestProblems

julia> n=63; maxit=1000; delta = 0.01; lambda = 20.0;

julia> bdata = beaminit(n, 0.0, lambda); x = bdata.x;

julia> u0 = x .* (1.0 .- x) .* (2.0 .- x);

julia> u0 .*= exp.(-10.0 * u0);

julia> FS = copy(u0); FPS = copy(bdata.D2);

julia> pout = ptcsol( FBeam!, u0, FS, FPS, BeamJ!; 
 rtol = 1.e-10, pdata = bdata, delta0 = delta, maxit = maxit);

julia> # It takes a few iterations to get there.
       length(pout.history)
25

julia> [pout.history[1:5] pout.history[21:25]]
5×2 Array{Float64,2}:
 6.31230e+01  9.75412e-01
 7.52624e+00  8.35295e-02
 8.31545e+00  6.58797e-04
 3.15455e+01  4.12697e-08
 3.66566e+01  6.29295e-12

julia> # We get the nonnegative steady state.
       maximum(pout.solution)
2.19086e+00
```
