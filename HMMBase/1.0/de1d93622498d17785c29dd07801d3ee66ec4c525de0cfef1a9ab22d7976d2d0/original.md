```
statdists(hmm) -> Vector{Vector}
```

Return the stationnary distribution(s) of `hmm`.   That is, the eigenvectors of transpose(hmm.A) with eigenvalues 1.
