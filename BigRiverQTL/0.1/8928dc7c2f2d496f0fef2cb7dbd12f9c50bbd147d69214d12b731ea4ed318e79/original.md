```
 kinship_4way(genmat::Array{Float64,2})
```

Computes a kinship for four-way cross data counting different alleles between two markers: ex. AB-AB=0; AB-AC=1; AB-CD=2,$\dots$ Note: In [R/qtl](https://cran.r-project.org/web/packages/qtl/qtl.pdf), genotypes are labeled as 1=AC; 2=BC; 3=AD; 4=BD by the function, `read.cross`.

# Argument

  * `genmat` : A matrix of genotypes for `four-way cross` $(1,2, \dots)$.          size(genematrix)= (p,n), for `p` genetic markers x `n` individuals(or lines).

# Output

Returns a n x n symmetric matrix containing 1's on the diagonal.
