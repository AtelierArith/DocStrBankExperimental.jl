kl_bicgstab( x0, b, atv, V, eta, ptv = nothing;       kl_store=nothing, side = "right", lmaxit = 10, pdata = nothing) 

C. T. Kelley, 2022

BiCGSTAB linear solver. Deals with preconditioning.  Uses bicgstab_base with is oblivious to that.

The code works and does what it needs to do, but ...

The user interface is unstable and, even worse, the nonlinear solvers are not hooked up yet.

The way this works it 

Input:

x0:  initial iterate, this is usually zero for nonlinear solvers

b: right hand side (duh!)

atv:  matrix-vector product which depends on precomputed data pdta       I expect you to use pdata most or all of the time, so it is not       an optional argument, even if it's nothing (at least for now).       If your mat-vec is just A*v, you have to write a function where       A is the precomputed data.       API for atv is av=atv(v,pdata)

V: a vector for me to store a Jacobian-vector product. It goes where     FPS would go in gmres. You are best served if V is Float64.

eta: Termination happens when ||b - Ax|| <= eta || b ||

ptv:  preconditioner-vector product, which will also use pdata. The       default is nothing, which is no preconditioning at all.       API for ptv is px=ptv(x,pdat) just like kl_gmres

Keyword arguments

kl_store: You have the option of giving me some room          for the vectors bicgstab needs to do its work. These in          which I will not overwrite and a couple of vectors I use          in the iteration. If you're only doing a linear solve, it          does no harm to let me allocate those vectores in kl_bicgstab.          The way to preallocate is `kl_store=kstore(n,"bicgstab")` where n          is the number of unknows. I call this myself in the initialization          phase if you don't do it ahead of me.

side: left or right preconditioning. The default is "right".

lmaxit: maximum number of linear iterations. The default is 10.

pdata: precomputed data. The default is nothing, but that ain't gonna         work well for nonlinear equations.

Output:

A named tuple (sol, reshist, lits, idid)

where

sol= final result reshist = residual norm history lits = number of iterations idid = status of the iteration        true -> converged        false -> failed to converge

### Examples from the docstrings for kl_bicgstab

In these examples you have the matrix and use

```
function atv(x, A)
    return A * x
end
```

to compute the matvec.

#### Three dimensional problem.

Will converge in the four iterations (worse than kl_gmres)

```jldoctest
julia> function atv(x, A)
           return A * x
       end
atv (generic function with 1 method)

julia> A = [0.001 0 0; 0 0.0011 0; 0 0 1.e4];

julia> V = zeros(3); b = [1.0; 1.0; 1.0]; x0 = zeros(3);

julia> gout.reshist
5-element Vector{Any}:
 1.73205e+00
 1.41421e+00
 3.21642e-03
 3.20321e-03
 4.98049e-13

julia> norm(b - A*gout.sol,Inf)
3.68594e-13
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

julia> u0 = zeros(size(f)); V = zeros(size(f));

julia> gout.reshist
4-element Vector{Any}:
 1.48252e+01
 2.90538e-02
 2.07823e-07
 2.17107e-17

julia> norm(gout.sol-ue,Inf)
8.88178e-16
```
