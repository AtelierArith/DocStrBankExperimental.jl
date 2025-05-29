```
default_alphabet(q::Int, T::Type)
```

  * if `q==2`, binary (0, 1)
  * if `3 <= q <= 4`, nucleotides without gaps
  * if `q==5`, nucleotides
  * if `5 < q <= 21`, amino acids
  * if `q>21`, fails
