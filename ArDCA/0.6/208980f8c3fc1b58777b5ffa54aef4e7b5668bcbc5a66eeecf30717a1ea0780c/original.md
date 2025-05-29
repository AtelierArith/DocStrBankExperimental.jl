```
dms_single_site(arnet::ArNet, arvar::ArVar, seqid::Int; pc::Float64=0.1)
```

Return a `q×L` matrix of containing `-log(P(mut))/log(P(seq))` for all single site mutants of the reference sequence `seqid`, and a vector of the indices of the residues of the reference sequence that contain gaps (i.e. the 21 amino-acid) for which the score has no sense and is set by convention to `+Inf`. A negative value indicate a beneficial mutation, a value 0 indicate the wild-type amino-acid.
