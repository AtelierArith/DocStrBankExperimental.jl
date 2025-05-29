```
mb03bd!(job::AbstractChar, defl::AbstractChar, compq::AbstractChar, qind::AbstractVector{Int64}, k::Integer, n::Integer, h::Integer, 
        ilo::Integer, ihi::Integer, s::AbstractVector{Int64}, a::Array{Float64, 3}, q::Array{Float64, 3}, alphar::AbstractVector{Float64}, 
        alphai::AbstractVector{Float64}, beta::AbstractVector{Float64}, scal::AbstractVector{Int64}, 
        liwork::Integer, ldwork::Integer) -> (info::Int64, iwarn::Int64)

mb03bd!(job::AbstractChar, defl::AbstractChar, compq::AbstractChar, qind::AbstractVector{Int64}, k::Integer, n::Integer, h::Integer, 
        ilo::Integer, ihi::Integer, s::AbstractVector{Int64}, a::Array{Float64, 3}, q::Array{Float64, 3}, alphar::AbstractVector{Float64}, 
        alphai::AbstractVector{Float64}, beta::AbstractVector{Float64}, scal::AbstractVector{Int64}, 
        iwork::AbstractVector{Int64}, dwork::AbstractVector{Float64}) -> (info::Int64, iwarn::Int64)
```

Find the eigenvalues of the generalized matrix product

```
          s[1]           s[2]                 s[k]
  A[:,:,1]     * A[:,:,2]     * ... * A[:,:,k]
```

where `A[:,:,h]` is upper Hessenberg and `A[:,:,i]`, `i <> h`, is upper triangular, using a double-shift version of the periodic QZ method. In addition, `A` may be reduced to periodic Schur form: `A[:,:,h]` is upper quasi-triangular and all the other factors `A[:,:,i]` are upper triangular. Optionally, the 2-by-2 triangular matrices corresponding to 2-by-2 diagonal blocks in `A[:,:,h]` are so reduced that their product is a 2-by-2 diagonal matrix.

If `compq = 'U'` or `compq = 'I'`, then the orthogonal factors are computed and stored in the array `Q` so that for `s[i] = 1`,

```
                T
    Q[:,:,i](in)   A[:,:,i](in)   Q[:,:,mod(i,k)+1](in)
                                                        T 
=   Q[:,:,i](out)  A[:,:,i](out)  Q[:,:,mod(i,k)+1](out),
```

and for `s[i] = -1`,

```
                         T
    Q[:,:,mod(i,k)+1](in)   A[:,:,i](in)   Q[:,:,i](in)
                                                        T 
=   Q[:,:,mod(i,k)+1](out)  A[:,:,i](out)  Q[:,:,i](out).
```

A partial generation of the orthogonal factors can be realized via the array `qind`.

See the SLICOT documentation of `MB03BD` for details.
