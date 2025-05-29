```
random_dropout(sites::AtomList{D, T}, ratio::Real) where {D, T}
random_dropout(ratio)
```

`sites`から`ratio * number of sites`の原子をランダムにドロップアウトします。ここで、`ratio` ∈ [0, 1]です。
