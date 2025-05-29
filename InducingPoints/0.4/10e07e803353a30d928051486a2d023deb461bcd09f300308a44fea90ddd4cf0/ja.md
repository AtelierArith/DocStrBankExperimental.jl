```
updateZ!([rng::AbstractRNG], Z::AbstractVector, alg::OnIPSA, X::AbstractVector; [kwargs...])
```

データ `X` とアルゴリズム `alg` を使用して誘導点 `Z` を更新します。一部のアルゴリズムには追加のキーワード引数が必要です。`InducingPoints` も参照してください。
