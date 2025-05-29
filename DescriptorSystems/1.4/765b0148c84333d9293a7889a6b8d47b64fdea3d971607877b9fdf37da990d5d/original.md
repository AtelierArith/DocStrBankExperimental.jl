```
gzeroinfo(sys; smarg, fast = false, prescale, atol = 0, atol1 = atol, atol2 = atol, 
          rtol = n*ϵ, offset = sqrt(ϵ)) -> (val, info)
```

Return for the descriptor system `sys = (A-λE,B,C,D)` the complex vector `val` containing  the finite and infinite Smith zeros of the system matrix pencil `S(λ)` 

```
          | A-λE | B | 
   S(λ) = |------|---| 
          |  C   | D |
```

and the named tuple `info` containing information on the Kronecker structure of the pencil `S(λ)`.  The values in `val` are called the *invariant zeros* of the pencil `S(λ)` and are the *transmission zeros* of the  transfer function matrix of `sys` if `A-λE` is *regular* and the descriptor system realization  `sys = (A-λE,B,C,D)` is *irreducible*. 

If `prescale = true`, a preliminary balancing of the descriptor system matrices is performed.  The default setting is `prescale = gbalqual(sys) > 10000`, where `gbalqual(sys)` is the  scaling quality of the descriptor system model `sys` (see [`gbalqual`](@ref)). 

For stability analysis purposes, a stability margin `smarg` can be specified for the finite zeros, in conjunction with a stability domain boundary offset `β` to numerically assess the  finite zeros  which belong to the boundary of the stability domain as follows:  in the continuous-time case, these are the finite zeros having real parts in the interval `[smarg-β, smarg+β]`, while in the discrete-time case, these are the finite zeros having moduli in the interva `[smarg-β, smarg+β]`. The default value of the stability margin `smarg` is `0` for a continuous-time system and  `1` for a discrete-time system.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The named tuple `info` contains the following information:

`info.nfz` is the number of finite eigenvalues of the pencil `S(λ)` (also the number of finite zeros of `sys`);

`info.niev` is the number of infinite eigenvalues of the pencil `S(λ)`;

`info.nisev` is the number of  *simple* infinite eigenvalues of the pencil `S(λ)`; 

`info.niz` is the number of infinite zeros of the system `sys`;

`info.nfsz` is the number of finite stable zeros, i.e., the finite zeros having real parts or moduli less than `smarg-β` for a continuous- or discrete-time system, respectively;

`info.nfsbz` is the number of finite zeros on the boundary of the            stability domain, i.e., the finite zeros           having real parts or moduli in the interval `[smarg-β, smarg+β]` for a continuous- or discrete-time system, respectively;

`info.nfuz` is the number of finite unstable zeros, i.e., the finite zeros having real parts or moduli greater than `smarg+β` for a continuous- or discrete-time system, respectively;

`info.nrank` is the normal rank of the pencil `S(λ)`;

`info.miev` is an integer vector, which contains the multiplicities            of the infinite eigenvalues of the pencil `S(λ)`              (also the dimensions of the elementary infinite blocks in the           Kronecker form of `S(λ)`);

`info.miz` is an integer vector, which contains the information on the              multiplicities of the infinite zeros of `S(λ)` as follows:             `S(λ)` has `info.mip[i]` infinite zeros of multiplicity `i`, and               is empty if `S(λ)` has no infinite zeros;

`info.rki` is an integer vector, which contains the *right Kronecker indices*           of the pencil `S(λ)` (empty for a regular pencil);

`info.lki` is an integer vector, which contains the *left Kronecker indices*          of the pencil `S(λ)` (empty for a regular pencil);

`info.regular` is set to `true`,  if the pencil `S(λ)` is regular and set to   `false`, if the pencil `S(λ)` is singular;

`info.stable` is set to `true`, if the pencil `S(λ)` has only stable                   finite zeros and all its infinite zeros are                  simple and  is set to `false` otherwise.

*Note:* The finite zeros and the finite eigenvalues of the pencil `S(λ)` are the same, but the multiplicities of infinite eigenvalues     are in excess with one to the multiplicities of infinite zeros. 

The computation of the zeros is performed by reducing the pencil `S(λ)` to an appropriate Kronecker-like form   using orthonal similarity transformations and involves rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `A`, `B`, `C` and `D`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A`, `E`, `B`, `C` and `D`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of `A` and `ϵ` is the  working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
