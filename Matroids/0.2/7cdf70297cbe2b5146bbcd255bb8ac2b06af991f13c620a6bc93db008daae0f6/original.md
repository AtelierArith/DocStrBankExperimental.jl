```
fuzzy_equal(M1::Matroid, M2::Matroid, reps::Int=1000)::Bool
```

This is a randomized test to see if two matroids are equal. If the result is `false`, they are definitely not equal. If the result is `true`, they probably are. 
