```
add(y, x, [α::Number = 1, β::Number = 1])
```

`y` と `x` を加算するか、より一般的には線形結合 `y * β + x * α` を構築します。

!!! note
    新しい型は四引数バージョンのみを実装するべきです。必要に応じて、二引数および三引数バージョンは `α` と `β` が `One` 型であることに特化することで区別できます。


参照: [`add!`](@ref) と [`add!!`](@ref)
