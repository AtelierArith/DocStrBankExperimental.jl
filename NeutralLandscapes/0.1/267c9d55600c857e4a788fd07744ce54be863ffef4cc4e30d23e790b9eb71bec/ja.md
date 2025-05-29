```
rand!(mat, alg) where {IT <: Integer}
```

行列 `mat` を、`alg` によって定義されたモデルに従って作成された風景で埋めます。`mask` 引数はブール値の行列を受け入れ、`nothing` でない場合は `mask!` に渡されます。
