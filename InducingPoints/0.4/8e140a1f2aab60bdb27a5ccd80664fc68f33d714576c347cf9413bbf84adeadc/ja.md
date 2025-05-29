```
updateZ!([rng::AbstractRNG], Z::AbstractVector, alg::OIPS, X::AbstractVector; kernel::Kernel)
```

データ `X` と OnlineIPSelection アルゴリズムを使用して誘導点 `Z` を更新します。追加のキーワード引数として `kernel` が必要です。
