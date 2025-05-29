```
Stoquastic(ham <: AbstractHamiltonian) <: AbstractHamiltonian
```

[`AbstractHamiltonian`](@ref) のラッパーで、すべての対角外行列要素 `v` を `-abs(v)` に置き換え、新しいハミルトニアンを *stoquastic* にします。

stoquastic ハミルトニアンはモンテカルロの符号問題を持ちません。エルミートな `ham` に対して、`Stoquastic(ham)` の最小固有値は `ham` の最小固有値以下です。
