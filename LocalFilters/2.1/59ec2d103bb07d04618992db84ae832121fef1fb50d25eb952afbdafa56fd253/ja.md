```
LocalFilters.bottom_hat!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

は、構造要素 `B` とオプションの平滑化要素 `C` を用いて `A` に適用されたボトムハットフィルタの結果で `dst` を上書きします。引数 `wrk` は内容が保持されないワークスペース配列です。引数 `A`、`dst`、および `wrk` は似ているが異なる配列でなければなりません。宛先 `dst` が返されます。

詳細については、[`bottom_hat`](@ref) を参照してください。
