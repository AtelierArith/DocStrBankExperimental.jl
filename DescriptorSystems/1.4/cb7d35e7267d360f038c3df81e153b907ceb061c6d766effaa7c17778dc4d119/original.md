```
gbalmr(sys, balance = false, matchdc = false, ord = missing, offset = √ϵ,
       atolhsv = 0, rtolhsv = nϵ, atolmin = atolhsv, rtolmin = rtolhsv, 
       atol = 0, atol1 = atol, atol2 = atol, rtol, fast = true) -> (sysr, hs)
```

Compute for a proper and stable descriptor system `sys = (A-λE,B,C,D)` with the transfer function matrix `G(λ)`, a reduced order realization `sysr = (Ar-λEr,Br,Cr,Dr)` and the vector `hs` of decreasingly  ordered Hankel singular values of the system `sys`. If `balance = true`, a balancing-based approach is used to determine a reduced order minimal realization  of the form `sysr = (Ar-λI,Br,Cr,Dr)`. For a continuous-time system `sys`, the resulting realization `sysr` is balanced, i.e., the controllability and observability grammians are equal and diagonal.  If additonally `matchdc = true`, the resulting `sysr` is computed using state rezidualization formulas  (also known as *singular perturbation approximation*) which additionally preserves the DC-gain of `sys`.  In this case, the resulting realization `sysr` is balanced (for both continuous- and discrete-time systems). If `balance = false`, an enhanced accuracy balancing-free approach is used to determine the  reduced order system `sysr`. 

If `ord = nr`, the resulting order of `sysr` is `min(nr,nrmin)`, where `nrmin` is the order of a minimal   realization of `sys` determined as the number of Hankel singular values exceeding `max(atolmin,rtolmin*HN)`, with `HN`, the Hankel norm of `G(λ)`. If `ord = missing`, the resulting order is chosen as the number of Hankel  singular values exceeding `max(atolhsv,rtolhsv*HN)`. 

To check the stability of the eigenvalues of the pencil `A-λE`, the real parts of eigenvalues must be less than `-β` for a continuous-time system or  the moduli of eigenvalues must be less than `1-β` for a discrete-time system, where `β` is the stability domain boundary offset.   The offset  `β` to be used can be specified via the keyword parameter `offset = β`.  The default value used for `β` is `sqrt(ϵ)`, where `ϵ` is the working machine precision. 

The keyword arguments `atol1`, `atol2`, and `rtol`, specify, respectively,  the absolute tolerance for the nonzero elements of `A`, `B`, `C`, `D`,   the absolute tolerance for the nonzero elements of `E`,   and the relative tolerance for the nonzero elements of `A`, `B`, `C`, `D` and `E`.   The default relative tolerance is `nϵ`, where `ϵ` is the working *machine epsilon*  and `n` is the order of the system `sys`. The keyword argument `atol` can be used  to simultaneously set `atol1 = atol` and `atol2 = atol`. 

If `E` is singular, the uncontrollable infinite eigenvalues of the pair `(A,E)` and the non-dynamic modes are elliminated using minimal realization techniques. The rank determinations in the performed reductions are based on rank revealing QR-decompositions with column pivoting  if `fast = true` or the more reliable SVD-decompositions if `fast = false`. 

Method:  For the order reduction of a standard system, the balancing-free method of [1] or  the balancing-based method of [2] are used. For a descriptor system the balancing related order reduction  methods of [3] are used. To preserve the DC-gain of the original system, the singular perturbation  approximation method of [4] is used in conjunction with the balancing-based or balancing-free approach of [5]. 

References

[1] A. Varga.      Efficient minimal realization procedure based on balancing.     In A. El Moudni, P. Borne, and S.G. Tzafestas (Eds.),      Prepr. of the IMACS Symp. on Modelling and Control of Technological      Systems, Lille, France, vol. 2, pp.42-47, 1991.

[2] M. S. Tombs and I. Postlethwaite.      Truncated balanced realization of a stable non-minimal state-space      system. Int. J. Control, vol. 46, pp. 1319–1330, 1987.

[3] T. Stykel.      Gramian based model reduction for descriptor systems.      Mathematics of Control, Signals, and Systems, 16:297–319, 2004.

[4] Y. Liu Y. and B.D.O. Anderson      Singular Perturbation Approximation of Balanced Systems,     Int. J. Control, Vol. 50, pp. 1379-1405, 1989.

[5] Varga A.     Balancing-free square-root algorithm for computing singular perturbation approximations.     Proc. 30-th IEEE CDC,  Brighton, Dec. 11-13, 1991, Vol. 2, pp. 1062-1065.
