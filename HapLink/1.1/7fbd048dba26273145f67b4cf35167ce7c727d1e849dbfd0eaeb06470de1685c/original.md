```
linkage(counts::AbstractArray{<:Integer, N}) where N
```

Calculates the linkage disequilibrium of a haplotype given its $N$-dimensional contingency matrix, `counts`.

`counts` is an $N$-dimensional array where the $N$th dimension represents the $N$th variant call locus within a haplotype. `findoccurrences` produces such an array.

# Extended help

`linkage(::AbstractArray{<:Integer, N})` calculates an unweighted linkage disequilibrium as given by Equation (6) of [Slatkin (1972)](https://doi.org/10.1093/genetics/72.1.157).

$$
D(1..N) = E\left( \prod_k^N i_k - P_k \right)
$$

where

  * $N$ is the number of variant loci
  * $D(1..N)$ is the linkage disequilibrium of all $N$ variant loci
  * $E$ is an operator returning the arithmetic mean of its argument over every read
  * $i_k$ is a function that returns $1$ if the $k$-th locus of the given read contains the reference allele, and returns $0$ otherwise.
  * $P_k$ is the probability of any read containing the reference allele in the $k$-th locus, i.e. the frequency at which the reference allele is found within the entire read set at the $k$-th locus
