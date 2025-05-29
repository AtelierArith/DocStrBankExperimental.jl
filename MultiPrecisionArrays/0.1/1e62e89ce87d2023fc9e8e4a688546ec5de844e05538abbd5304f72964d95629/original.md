mpglu!(MPG::MPGEFact, A::AbstractArray{TW,2}) where TW <: Real Overwrite a multiprecision factorization MPF to reuse the storage to make a multiprecision of a new matrix A.

This will, of course, trash the original factorization.

To use this do

```
MPG=mpglu!(MPG,A)
```

Simply using

```
mpglu!(MPG,A) # Don't do this.
```

(ie without explicitly returning MPG)

may not do what you want because the multiprecision factorization structure is immutable and MPF.AF.info cannot be changed.

Reassigning MPG works and resuses almost all of the storage in the original array
