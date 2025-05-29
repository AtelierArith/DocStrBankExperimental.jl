```
hascommoninds(A, B; kwargs...)

hascommoninds(B; kwargs...) -> f::Function
```

ITensor またはインデックスの集合 `A` と `B` に共通のインデックスがあるかどうかを確認します。

インデックスの集合 `B` のみが渡された場合、関数 `f` を返します。これは `f(A) = hascommoninds(A, B; kwargs...)` となります。
