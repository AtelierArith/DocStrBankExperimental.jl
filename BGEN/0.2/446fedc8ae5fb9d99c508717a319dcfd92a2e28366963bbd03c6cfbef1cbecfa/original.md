```
clear!(g::Genotypes)
clear!(v::BgenVariant)
```

Clears cached decompressed byte representation, probabilities, and dose. If `BgenVariant` is given, it removes the corresponding `.genotypes` altogether.
