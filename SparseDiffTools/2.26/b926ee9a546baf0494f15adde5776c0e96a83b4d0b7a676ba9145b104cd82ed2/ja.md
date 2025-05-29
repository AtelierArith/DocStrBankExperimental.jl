```
init_jacobian(cache::AbstractMaybeSparseJacobianCache;
    preserve_immutable::Val = Val(false))
```

キャッシュに基づいてヤコビアンを初期化します。可能であればスパースヤコビアンを使用します。

`preserve_immutable` が `true` の場合、返されるヤコビアンは不変である可能性があり、これは `StaticArrays` のような不変の入力がある場合に関連します。
