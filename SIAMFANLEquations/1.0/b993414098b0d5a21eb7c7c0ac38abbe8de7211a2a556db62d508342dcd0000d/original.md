kl_gmres(x0, b, atv, V, eta, ptv=nothing; kl_store=nothing;               orth = "cgs2", side="right", lmaxit=-1, pdata=nothing)

C. T. Kelley, 2022

Gmres linear solver. Handles preconditioning and restarts.  Uses gmres_base which is completely oblivious to these things.

The deal is

Input:

x0:  initial iterate, this is usually zero for nonlinear solvers

b: right hand side (duh!)

atv:  matrix-vector product which depends on precomputed data pdta       I expect you to use pdata most or all of the time, so it is not       an optional argument, even if it's nothing (at least for now).        If your mat-vec is just A*v, you have to write a function where        A is the precomputed data.       API for atv is `av=atv(v,pdata)`

V:  Preallocated n x K array for the Krylov vectors. I store the initial     normalized residual in column 1, so  you have at most K-1 iterations     before gmres_base returns a failure. kl_gmres will handle the      restarts and, if lmaxit > 0, keep going until you hit lmaxit GMRES     iterations. You may allocate V in Float32 and save on storage. The     benefit from doing this is not dramatic in terms of CPU time.

eta: Termination happens when ||b - Ax|| <= eta || b ||

ptv:  preconditioner-vector product, which will also use pdata. The       default is nothing, which is no preconditioning at all.       API for ptv is px=ptv(x,pdata)

Keyword arguments

kl_store: You have the option (don't do it!) of giving me some room          for the vectors gmres needs. These include copies of x0 and b,          which I will not overwrite and a couple of vectors I use          in the iteration. If you're only doing a linear solve, PLEASE          let me allocate those vectores in kl_gmres. For computing a          Newton step or for repeated solves,          the way to do this is `kl_store=kstore(n,"gmres")` where n          is the number of unknows. I call this myself in the initialization          phase if you don't do it ahead of me.

```
     Be very careful with this. kl_store is use to store the solution
     to avoid overwriting the initial iterate. This means that
     two calls to kl_gmres with the same kl_store will step on the
     solution coming from the first call. If you let me allocate it
     then it happens in local scope and will do no harm.
```

pdata: precomputed data. The default is nothing, but that ain't gonna         work well for nonlinear equations.

orth: your choice of the wise default, classical Gram-Schmidt twice,        or something slower and less stable. Those are classical once (really        bad) or a couple variants of modified Gram-Schmidt. mgs2 is what I        used in my old matlab codes. Not terrible, but far from great.

side: left or right preconditioning. The default is "right".

lmaxit: maximum number of linear iterations. The default is -1, which         means that the maximum number of linear iterations is K-1, which         is all V will allow without restarts. If lmaxit > K-1, then the         iteration will restart until you consume lmaxit iterations or         terminate successfully.

Other parameters on the way.

Output:

A named tuple (sol, reshist, lits, idid)

where

sol= final result reshist = residual norm history lits = number of iterations idid = status of the iteration        true -> converged         false -> failed to converge

### Examples from the docstrings for kl_gmres

In these examples you have the matrix and use 

```
function atv(x, A)
    return A * x
end
```

to compute the matvec.

#### Three dimensional problem.

Will converge in the correct three iterations only if you orthogonalize with CGS twice. 

```jldoctest
julia> function atv(x, A)
           return A * x
       end
atv (generic function with 1 method)

julia> A = [0.001 0 0; 0 0.0011 0; 0 0 1.e4];

julia> V = zeros(3, 10); b = [1.0; 1.0; 1.0]; x0 = zeros(3);

julia> gout = kl_gmres(x0, b, atv, V, 1.e-10; pdata = A);

julia> gout.reshist
4-element Array{Float64,1}:
 1.73205e+00
 1.41421e+00
 6.72673e-02
 1.97712e-34

julia> norm(b - A*gout.sol,Inf)
1.28536e-10
```

#### Integral equation. Notice that pdata has the kernel of the

operator and we do the matvec directly. Just like the previous example. We put the grid information and, for this artifical example, the solution in the precomputed data.

```jldoctest
julia> function integop(u, pdata)
           K = pdata.K
           return u - K * u
       end
integop (generic function with 1 method)

julia> function integopinit(n)
           h = 1 / n
           X = collect(0.5*h:h:1.0-0.5*h)
           K = [ker(x, y) for x in X, y in X]
           K .*= h
           sol = [usol(x) for x in X]
           f = sol - K * sol
           pdata = (K = K, xe = sol, f = f)
           return pdata
       end
integopinit (generic function with 1 method)

julia> function usol(x)
           return exp.(x) .* log.(2.0 * x .+ 1.0)
       end
usol (generic function with 1 method)

julia> function ker(x, y)
           ker = 0.1 * sin(x + exp(y))
       end
ker (generic function with 1 method)

julia> n=100; pdata = integopinit(n); ue = pdata.xe; f=pdata.f;

julia> u0 = zeros(size(f)); V = zeros(n, 20); V32=zeros(Float32,n,20);

julia> gout = kl_gmres(u0, f, integop, V, 1.e-10; pdata = pdata);

julia> gout32 = kl_gmres(u0, f, integop, V32, 1.e-10; pdata = pdata);

julia> [norm(gout.sol-ue,Inf) norm(gout32.sol-ue,Inf)]
1×2 Array{Float64,2}:
 4.44089e-16  2.93700e-07

julia> [gout.reshist gout32.reshist]
4×2 Array{Float64,2}:
 1.48252e+01  1.48252e+01
 5.52337e-01  5.52337e-01
 1.77741e-03  1.77742e-03
 1.29876e-19  8.73568e-11
```
