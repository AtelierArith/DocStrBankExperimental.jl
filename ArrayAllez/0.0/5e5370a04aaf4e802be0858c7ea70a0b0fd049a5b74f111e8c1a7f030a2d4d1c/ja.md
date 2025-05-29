```
iscale!(A, b::Number) ≈ A ./ b
iscale!(A, v::Vector) ≈ A ./ v      # A::Matrix
iscale!(A, r::Adjoint) ≈ A ./ r     # r::RowVector / Transpose etc.
iscale!(A, B) ≈ A ./ B
```

これらのそれぞれに対して、非破壊的だがおそらく加速された `iscale_(A, ...)` と、単純なブロードキャスティングの `iscale0(A, ...)` もあります。最後に、両方の引数を変更する `iscale!!(A, x)` がありますが、これはひどいアイデアかもしれません。
