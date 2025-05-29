```
gpoleinfo(sys; smarg, fast = false, atol = 0, atol1 = atol, atol2 = atol, 
          rtol = n*ϵ, offset = sqrt(ϵ)) -> (val, info)
```

Return for the descriptor system `sys = (A-λE,B,C,D)` the complex vector `val` containing  the finite and infinite zeros of the system pole pencil `P(λ) := A-λE` and the named tuple `info` containing information on  the eigenvalue structure of the pole pencil `P(λ)`. The values in `val` are the *poles* of the  transfer function matrix of `sys`, if `A-λE` is *regular* and the  descriptor system realization `sys = (A-λE,B,C,D)` is *irreducible*.  If the pencil `A-λE` is singular, `val` also contains `NaN` elements, whose number is the rank deficiency of the pencil  `A-λE`.

For stability analysis purposes, a stability margin `smarg` can be specified for the finite eigenvalues, in conjunction with a stability domain boundary offset `β` to numerically assess the  finite eigenvalues  which belong to the boundary of the stability domain as follows:  in the continuous-time case, these are the finite eigenvalues having real parts in the interval `[smarg-β, smarg+β]`, while in the discrete-time case, these are the finite eigenvalues having moduli in the interval `[smarg-β, smarg+β]`. The default value of the stability margin `smarg` is `0` for a continuous-time system and  `1` for a discrete-time system.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The named tuple `info` contains the following information:

`info.nfev` is the number of finite eigenvalues of the pencil `A-λE` (also the number of finite poles of `sys`);

`info.niev` is the number of infinite eigenvalues of the pencil `A-λE`;

`info.nisev` is the number of *simple* infinite eigenvalues of the pencil `A-λE` (also known as non-dynamic modes); 

`info.nip` is the number of infinite poles of the system `sys`;

`info.nfsev` is the number of finite stable eigenvalues, i.e., the finite eigenvalues having real parts or moduli less than `smarg-β` for a continuous- or discrete-time system, respectively;

`info.nfsbev` is the number of finite eigenvalues on the boundary of the            stability domain, i.e., the finite eigenvalues           having real parts or moduli in the interval `[smarg-β, smarg+β]` for a continuous- or discrete-time system, respectively;

`info.nfuev` is the number of finite unstable eigenvalues, i.e., the finite eigenvalues having real parts or moduli greater than `smarg+β` for a continuous- or discrete-time system, respectively;

`info.nhev` is the number of *hidden* eigenvalues set to `NaN`          (can be nonzero only if the pencil `A-λE` is singular);  

`info.nrank` is the normal rank of the pencil `A-λE`;

`info.miev` is an integer vector, which contains the multiplicities            of the infinite eigenvalues of the pencil `A-λE` as follows:           the `i`-th element `info.miev[i]` is the order of an infinite elementary divisor            (i.e., the multiplicity of an infinite eigenvalue) and            the number of infinite poles is the sum of the components of `info.miev`;  

`info.mip` is an integer vector, which contains the information on the              multiplicities of the infinite zeros of `A-λE` as follows:             the `i`-th element `info.mip[i]` is equal to `k-1`, where `k` is the order of an infinite elementary               divisor with `k > 0` and the number of infinite poles is the sum of the components of `info.mip`; 

`info.rki` is an integer vector, which contains the *right Kronecker indices*             of the pencil `A-λE` (empty for a regular pencil);

`info.lki` is an integer vector, which contains the *left Kronecker indices*            of the pencil `A-λE` (empty for a regular pencil);

`info.regular` is set to `true`,  if the pencil `A-λE` is regular and set to   `false`, if the pencil `A-λE` is singular;

`info.proper` is set to `true`, if the pencil `A-λE` is regular and all its infinite                   eigenvalues are simple (has only non-dynamic modes), or                   is set to `false`, if the pencil `A-λE` is singular or has higher order infinite eigenvalues;

`info.stable` is set to `true`, if the pencil `A-λE` is regular, has only stable                   finite eigenvalues and all its infinite eigenvalues are                  simple (has only non-dynamic modes), and  is set to `false` otherwise.

*Note:* The finite poles and the finite eigenvalues of the pencil `P(λ)` are the same,  but the multiplicities of infinite eigenvalues of `P(λ)` are in excess with one to the multiplicities of infinite poles.

For the reduction of the pencil `P(λ)` to an appropriate Kronecker-like form   orthonal similarity transformations are performed, which involve rank decisions based on rank revealing QR-decompositions with column pivoting,  if `fast = true`, or, the more reliable, SVD-decompositions, if `fast = false`. 

The keyword arguements `atol1`, `atol2`  and `rtol` specify the absolute tolerance for the nonzero elements of `A`, the absolute tolerance for the nonzero elements of `E`,  and the relative tolerance for the nonzero elements of `A` and `E`, respectively.  The default relative tolerance is `n*ϵ`, where `n` is the size of `P(λ)`, and `ϵ` is the  working machine epsilon.  The keyword argument `atol` can be used to simultaneously set `atol1 = atol` and `atol2 = atol`. 
