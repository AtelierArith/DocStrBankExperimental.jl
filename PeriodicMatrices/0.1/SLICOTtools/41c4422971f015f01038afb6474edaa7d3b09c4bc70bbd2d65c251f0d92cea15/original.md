```
mb03kd!(compq::AbstractChar, strong::AbstractChar, k::Integer, nc::Integer, kschur::Integer, n::AbstractVector{Int64}, ni::AbstractVector{Int64}, 
        s::AbstractVector{Int64}, select::AbstractVector{BlasInt}, t::AbstractVector{Float64}, ldt::AbstractVector{Int64}, ixt::AbstractVector{Int64}, 
        q::AbstractVector{Float64}, ldq::AbstractVector{Int64}, ixq::AbstractVector{Int64}, tol::Float64, ldwork::Integer) -> (m::Int64, info::Int64)
```

Reorder the diagonal blocks of the formal matrix product

```
 T22_k^s[k] * T22_k-1^s[k-1] * ... * T22_1^s[1],                (1)
```

of length `k`, in the generalized periodic Schur form,

```
          [  T11_i  T12_i  T13_i  ]
    T_i = [    0    T22_i  T23_i  ],    i = 1, ..., k,          (2)
          [    0      0    T33_i  ]
```

where

  * the submatrices `T11_i` are `ni(i+1)-by-ni(i)`, if `s[i] = 1`, or `ni(i)-by-ni(i+1)`, if `s[i] = -1`, and contain dimension-induced infinite eigenvalues,
  * the submatrices `T22_i` are `nc-by-nc` and contain core eigenvalues, which are generically neither zero nor infinite,
  * the submatrices `T33_i` contain dimension-induced zero eigenvalues,

such that the `m` selected eigenvalues pointed to by the integer vector `select` end up in the leading part of the matrix sequence `T22_i`.

Given that `n[i] = n[i+1]` for all `i` where s`[i] = -1`, the `T11_i` are void and the first `m` columns of the updated orthogonal transformation matrix sequence `Q_1, ..., Q_k` span a periodic deflating subspace corresponding to the same eigenvalues.

If `compq = 'U'` or `compq = 'I'`, then the orthogonal factors are computed and stored in the array `Q` so that for `s[i] = 1`,

```
           T
    Q_i(in)  T_i(in) Q_(mod(i,k)+1)(in)
                                          T 
=   Q_i(out) T_i(out)  Q_(mod(i,k)+1)(out),
```

and for `s[i] = -1`,

```
                      T
    Q_(mod(i,k)+1)(in)   T_i(in)   Q_i(in)
                                           T 
=   Q_(mod(i,k)+1)(out)  T_i(out)  Q_i(out).
```

See the SLICOT documentation of `MB03KD` for details.
