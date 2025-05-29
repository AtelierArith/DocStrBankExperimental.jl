```
init_jacobian(cache::AbstractMaybeSparseJacobianCache)
```

キャッシュに基づいてヤコビアンを初期化します。可能であればスパースヤコビアンを使用します。

!!! note
    この関数は提供されたヤコビアンプロトタイプをエイリアスしません。常に副作用なしに変更可能な新しいヤコビアンを初期化します。

