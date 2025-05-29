```
TaylorVector{N,T}
```

`N`項のテイラー級数のベクトルを表すデータ構造。各要素は`NTuple{N,T}`です。

```
TaylorVector(T, N::Integer, n::Integer)
```

`n`個の`NTuple{N,T}`のベクトルを作成します。
