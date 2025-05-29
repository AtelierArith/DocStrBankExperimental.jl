```
solveQP!(dmat::AbstractMatrix{T}, dvec::AbstractArray{T}, Amat::AbstractMatrix{T}, bvec::AbstractArray{T}; meq::Int = 0, factorized::Bool = false)::Tuple{AbstractArray{T},AbstractArray{T},T,AbstractArray{Int},Int,AbstractArray{Int}}
```

This routine implements the dual method of Goldfarb and Idnani (1982, 1983) for solving quadratic programming problems of the form

```
     minimize  -d^T x + 1/2 *  x^T D x
     where   A1^T x  = b1
             A2^T x >= b2
```

the matrix D is assumed to be positive definite.  Especially,    w.l.o.g. D is assumed to be symmetric.

# Input parameter:

  * `dmat`   nxn matrix, the matrix D from above (typically Float64)      The user has two possibilities:      a) Give D (factorized = false), in this case we use routines from LINPACK         to decompose D.      b) To get the algorithm started we need R^-1, where D=R^TR.         So if it is cheaper to calculate R^-1 in another way (D may         be a band matrix) then with the general routine, the user         may pass R^{-1}.  Indicated by factorized = true.
  * `dvec`   nx1 vector, the vector d from above (typically Float64)      contains on exit the solution to the initial, i.e.,      unconstrained problem
  * `Amat`   nxq matrix, the matrix A from above (typically Float64) [ A=(A1 A2)^T ]       ENTRIES CORRESPONDING TO EQUALITY CONSTRAINTS MAY HAVE          CHANGED SIGNES ON EXIT.
  * `bvec`   qx1 vector, the vector of constants b in the constraints (typically Float64)      [ b = (b1^T b2^T)^T ]      ENTRIES CORRESPONDING TO EQUALITY CONSTRAINTS MAY HAVE          CHANGED SIGNES ON EXIT.
  * `meq::Int=0`  the number of equality constraints, 0 <= meq <= q.

# Output parameter is a Tuple composed of:

1. sol   nx1 the final solution (x in the notation above)
2. lagr  qx1 the final Lagrange multipliers
3. crval scalar, the value of the criterion at the minimum
4. iact  qx1 vector, the constraints which are active in the final    fit (int)
5. nact  scalar, the number of constraints active in the final fit (int)
6. iter  2x1 vector, first component gives the number of "main"     iterations, the second one says how many constraints were    deleted after they became active
