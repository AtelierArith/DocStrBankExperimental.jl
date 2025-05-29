```
LocalFilters.top_hat!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

は、構造要素 `B` を用いて `A` に適用されたトッパーフィルタの結果で `dst` を上書きし、`wrk` を作業スペースとして使用しますが、その内容は保持されません。引数 `A`、`dst`、および `wrk` は似ているが異なる配列でなければなりません。宛先 `dst` が返されます。

詳細については、[`top_hat`](@ref) を参照してください。
