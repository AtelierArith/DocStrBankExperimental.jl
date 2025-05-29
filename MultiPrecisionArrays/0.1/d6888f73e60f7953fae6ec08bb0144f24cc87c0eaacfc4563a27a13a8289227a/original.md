mplu!(MPF::MPLFact,A::AbstractArray{TW,2}) where TW <: Real

Overwrite a multiprecision factorization MPF to reuse the storage to make a multiprecision of a new matrix A.

This will, of course, trash the original factorization.

To use this do

```
MPF=mplu!(MPF,A)
```

Simply using 

```
mplu!(MPF,A) # Don't do this!
```

(ie without explicitly returning MPF)

may not do what you want because the multiprecision factorization structure is immutable and MPF.AF.info cannot be changed.

Reassigning MPF works and resuses almost all of the storage in the  original array.

If you want to use static arrays with this stuff, use the  mutable @MArray constructor
