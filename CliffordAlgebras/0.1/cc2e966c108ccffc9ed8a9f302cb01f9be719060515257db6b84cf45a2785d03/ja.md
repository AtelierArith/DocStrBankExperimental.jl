```
Λᵏ(::MultiVector, ::Val{k}) where k
Λᵏ(::MultiVector, k::Integer)
```

MultiVectorをkベクトルに射影します。grade(mv,k)に似ていますが、@generatedコードとコンパイル時最適化を使用します。
