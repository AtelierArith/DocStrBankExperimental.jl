```
solveQPcompact(dmat::AbstractMatrix{T}, dvec::AbstractArray{T}, Amat::AbstractMatrix{T}, Aind::AbstractMatrix{Int}, bvec::AbstractArray{T}; meq::Int = 0, factorized::Bool = false)::Tuple{AbstractArray{T},AbstractArray{T},T,AbstractArray{Int},Int,AbstractArray{Int}}
```

This routine uses the Goldfarb/Idnani algorithm to solve the   following minimization problem:

```
    minimize  -d^T x + 1/2 *  x^T D x
    where   A1^T x  = b1
            A2^T x >= b2
```

the matrix D is assumed to be positive definite.  Especially,   w.l.o.g. D is assumed to be symmetric.

# Input parameter

  * `dmat`   nxn matrix, the matrix D from above (dp)      The user has two possibilities:      a) Give D (factorized=false), in this case we use routines from LINPACK         to decompose D.      b) To get the algorithm started we need R^-1, where D=R^TR.         So if it is cheaper to calculate R^-1 in another way (D may         be a band matrix) then with the general routine, the user         may pass R^{-1}.  Indicated by factorized = true.
  * `dvec`   nx1 vector, the vector d from above (typically Float64). Copied and thus unmodified.
  * `Amat`   lxq matrix (typically of Float64). Copied and thus unmodified.
  * `Aind`  (l+1)xq matrix (Int)      these two matrices store the matrix A in compact form. the format      is: [ A=(A1 A2)^T ]        Aind(1,i) is the number of non-zero elements in column i of A.        Aind(k,i) for k>=2, is equal to j if the (k-1)-th non-zero                   element in column i of A is A(i,j).        Aind(k,i) for k>=1, is equal to the k-th non-zero element                   in column i of A.
  * `bvec`   qx1 vector, the vector of constants b in the constraints (typically Float64)      [ b = (b1^T b2^T)^T ]. Copied and thus unmodified.
  * `meq::Int=0`   the number of equality constraints, 0 <= meq <= q.

# Output parameters as a Tuple

1. sol   nx1 the final solution (x in the notation above)
2. lagr  qx1 the final Lagrange multipliers
3. crval scalar, the value of the criterion at the minimum
4. iact  qx1 vector, the constraints which are active in the final    fit (int)
5. nact  scalar, the number of constraints active in the final fit (int)
6. iter  2x1 vector, first component gives the number of "main"    iterations, the second one says how many constraints were    deleted after they became active

```
# Tip
```

Amat and Aind may be created from a Julia sparse matrix through the convertSparse(A) function where A is a standard Julia sparse matrix.
