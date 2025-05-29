```
character(λ::Partition, μ::Partition)
```

Compute the character $\chi^{\lambda(\mu)}$ of the partition `μ` in the `λ`th irreducible representation ("irrep") of the symmetric group $S_n$.

Implements the Murnaghan-Nakayama algorithm as described in:

```
Dan Bernstein,
"The computational complexity of rules for the character table of Sn",
Journal of Symbolic Computation, vol. 37 iss. 6 (2004), pp 727-748.
doi:10.1016/j.jsc.2003.11.001
```
