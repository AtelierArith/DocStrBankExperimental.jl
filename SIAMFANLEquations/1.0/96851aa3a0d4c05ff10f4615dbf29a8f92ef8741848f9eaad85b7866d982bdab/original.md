```
nsoli(F!, x0, FS, FPS, Jvec=dirder; rtol=1.e-6, atol=1.e-12,
           maxit=20, lmaxit=-1, lsolver="gmres", eta=.1,
           fixedeta=true, Pvec=nothing, pside="right",
           armmax=10, dx = 1.e-7, armfix=false, pdata = nothing,
           printerr = true, keepsolhist = false, 
           Krylov_Data = nothing, stagnationok=false)
```

)

C. T. Kelley, 2022

Julia versions of the nonlinear solvers from my SIAM books.  Herewith: nsoli

You must allocate storage for the function and the Krylov basis in advance –> in the calling program <– ie. in FS and FPS

Inputs:

  * F!: function evaluation, the ! indicates that F! overwrites FS, your   preallocated storage for the function.

    So FS=F!(FS,x) or FS=F!(FS,x,pdata) returns FS=F(x)

    Your function MUST have –> return FS <– at the end.   See the examples in the docstrings

  * x0: initial iterate

  * FS: Preallocated storage for function. It is a vector of size N

    You should store it as (N) and design F! to use vectors of size (N). If you use (N,1) consistently instead, the solvers may work, but I make no guarantees.
  * FPS: preallocated storage for the Krylov basis. It is an N x m matrix where      you plan to take at most m-1 GMRES iterations before a restart.

  * Jvec: Jacobian vector product, If you leave this out the   default is a finite difference directional derivative.

    So, FP=Jvec(v,FS,x) or FP=Jvec(v,FS,x,pdata) returns FP=F'(x) v. 

    (v, FS, x) or (v, FS, x, pdata) must be the argument list,    even if FP does not need FS.   One reason for this is that the finite-difference derivative   does and that is the default in the solver.
  * Precision: Lemme tell ya 'bout precision. I designed this code for    full precision functions and linear algebra in any precision you want.    You can declare FPS as Float64 or Float32 and nsoli    will do the right thing. Float16 support is there, but not working well.

    If the Jacobian is reasonably well conditioned, you can cut the cost   of orthogonalization and storage (for GMRES) in half with no loss.    There is no benefit if your linear solver is not GMRES or if    orthogonalization and storage of the Krylov vectors is only a   small part of the cost of the computation. So if your preconditioner   is good and you only need a few Krylovs/Newton, reduced precision won't   help you much.

    BiCGSTAB does not benefit from reduced precision.

---

Keyword Arguments (kwargs):

rtol and atol: relative and absolute error tolerances

maxit: limit on nonlinear iterations

lmaxit: limit on linear iterations. If lmaxit > m-1, where FPS has m columns, and you need more than m-1 linear iterations, then GMRES  will restart. 

The default is -1 for GMRES. This means that you'll take m-1 iterations,  where size(V) = (n,m), and get no restarts. For BiCGSTAB the default is 10.

lsolver: the linear solver, default = "gmres"

Your choices will be "gmres" or "bicgstab". However, gmres is the only option for now.

eta and fixed eta: eta > 0 or there's an error

The linear solver terminates when ||F'(x)s + F(x) || <= etag || F(x) ||

where 

etag = eta if fixedeta=true

etag = Eisenstat-Walker as implemented in book if fixedeta=false

The default, which may change, is eta=.1, fixedeta=true

Pvec: Preconditioner-vector product. The rules are similar to Jvec     So, Pv=Pvec(v,x) or Pv=Pvec(v,x,pdata) returns P(x) v where     P(x) is the preconditioner. You must use x as an input even     if your preconditioner does not depend on x

pside: apply preconditioner on pside, default = "right". I do not       recommend "left". See Chapter 3 for the story on this.

armmax: upper bound on step size reductions in line search

dx: default = 1.e-7

difference increment in finite-difference derivatives       h=dx*norm(x,Inf)+1.e-8

armfix: default = false

The default is a parabolic line search (ie false). Set to true and the step size will be fixed at .5. Don't do this unless you are doing experiments for research.

pdata:

precomputed data for the function, Jacobian-vector, and Preconditioner-vector products.  Things will go better if you use this rather than hide the data  in global variables within the module for your function/Jacobian

If you use pdata in any of F!, Jvec, or Pvec, you must use in in all of them.

printerr: default = true

I print a helpful message when the solver fails. To suppress that message set printerr to false.

keepsolhist: default = false

Set this to true to get the history of the iteration in the output tuple. This is on by default for scalar equations and off for systems. Only turn it on if you have use for the data, which can get REALLY LARGE.

Krylov_Data: default = nothing

This is a structure where I put the internal storage for the solvers. You can (but probably should not) preallocate this your self with the nkl_init function.

Krylov_Data 

= nkl_init(n,lsolver)

This is a dangerous thing to mess with and I only recommend it if  the allocations in nsoli become a problem in continuation or IVP integration. Krylov_Data is where I store the solution at the end of the iteration and if you reuse it without copying the solution to somewhere else, you'll lose it and it will be overwritten with the new solution. The continuation case study uses this and you  should look at that to see what I did.

stagnationok: default = false

Set this to true if you want to disable the line search and either observe divergence or stagnation. This is only useful for research or writing a book.

Output:

  * A named tuple (solution, functionval, history, stats, idid,              errcode, solhist)

where

– solution = converged result

– functionval = F(solution)

– history = the vector of residual norms (||F(x)||) for the iteration

– stats = named tuple of the history of (ifun, ijac, iarm, ikfail), the  number of functions/Jacobian-vector prods/steplength reductions/linear solver failures at each iteration. Linear solver failures DO NOT mean that the nonlinear solver will fail. You should look at this stat if, for example, the line search fails. Increasing the size of FPS and/or lmaxit might solve the problem.

I do not count the function values for a finite-difference derivative because they count toward a Jacobian-vector product.

– idid=true if the iteration succeeded and false if not.

– errcode = 0 if the iteration succeeded

```
    = -1 if the initial iterate satisfies the termination criteria

    = 10 if no convergence after maxit iterations

    = 1  if the line search failed
```

– solhist:

```
  This is the entire history of the iteration if you've set
  keepsolhist=true
```

solhist is an N x K array where N is the length of x and K is the number of iteration + 1. So, for scalar equations, it's a row vector.

---

### Example for nsoli

#### Simple 2D problem.

You should get the same results as for nsol.jl because GMRES will solve the equation for the step exactly in two iterations. Finite difference Jacobians and analytic Jacobian-vector products for full precision and finite difference Jacobian-vector products for single precision.

BiCGSTAB converges in 5 iterations and each nonlinear iteration costs two Jacobian-vector products. Note that the storage for the Krylov space in GMRES (jvs) is replace by a single vector (fpv) when BiCGSTAB is the linear solver.

```jldoctest
julia> function f!(fv,x)
       fv[1]=x[1] + sin(x[2])
       fv[2]=cos(x[1]+x[2])
       return fv
       end
f! (generic function with 1 method)

julia> function JVec(v, fv, x)
       jvec=zeros(2);
       p=-sin(x[1]+x[2])
       jvec[1]=v[1]+cos(x[2])*v[2]
       jvec[2]=p*(v[1]+v[2])
       return jvec
       end
JVec (generic function with 1 method)

julia> x0=ones(2); fv=zeros(2); jv=zeros(2,2); 

julia> jv32=zeros(Float32,2,2);

julia> jvs=zeros(2,3); jvs32=zeros(Float32,2,3);

julia> nout=nsol(f!,x0,fv,jv; sham=1);

julia> kout=nsoli(f!,x0,fv,jvs,JVec; 
                  fixedeta=true, eta=.1, lmaxit=2);

julia> kout32=nsoli(f!,x0,fv,jvs32; 
                    fixedeta=true, eta=.1, lmaxit=2);

julia> [nout.history kout.history kout32.history]
5×3 Array{Float64,2}:
 1.88791e+00  1.88791e+00  1.88791e+00
 2.43119e-01  2.43120e-01  2.43119e-01
 1.19231e-02  1.19231e-02  1.19230e-02
 1.03266e-05  1.03261e-05  1.03264e-05
 1.46388e-11  1.40862e-11  1.39825e-11

julia> fpv=zeros(2);

julia> koutb=nsoli(f!,x0,fv,fpv,JVec; 
            fixedeta=true, eta=.1, lmaxit=2, lsolver="bicgstab");

julia> koutb.history
6-element Vector{Float64}:
 1.88791e+00
 2.43120e-01
 1.19231e-02
 4.87500e-04
 7.54236e-06
 3.84646e-07
```
