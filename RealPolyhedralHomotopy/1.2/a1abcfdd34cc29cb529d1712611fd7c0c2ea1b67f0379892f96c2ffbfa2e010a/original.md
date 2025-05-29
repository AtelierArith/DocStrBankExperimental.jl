```
rph_track(B::Binomial_system_data, F::System; Certification = false)
```

Return the output of tracking the real solutions of a given list of binomial systems to the target system.

# Arguments

  * `B` : The object `Binomial_system_data` obtained from `generate_binomials(F)`.
  * `F` : The target system for the real polyhedral homotopy.

```julia
@var x y;
F = System([-1 - 24000*y + x^3, -9 + 50*x*y - 1*y^2]);
B = generate_binomials(F);
realSols = rph_track(B,F)
```

```
4-element Vector{Vector{Float64}}:
 [-1095.4451129504978, -54772.25548320812]
 [1095.4451137838312, 54772.255524874796]
 [8.111114476617955, 0.02219298606763958]
 [-8.103507635567631, -0.02221382112196499]
```

  * The optional argument `Certification` certifies that all real solutions to a patchedworked system are found.

This is done by an a posteriori certification for numerical approximations obtained by the real polyhedral homotopy. When the real polyhedral homotopy root-finding is certified, it returns a list of solutions to the target and `1`; otherwise, it returns `0`. The default value for the option is false.

```julia
realSols = rph_track(B,F; Certification = true)
```

```
([[-1095.4451129504978, -54772.25548320812], [1095.4451137838312, 54772.255524874796], [8.111114476617955, 0.02219298606763958], [-8.103507635567631, -0.022213821121964985]], 1)
```
