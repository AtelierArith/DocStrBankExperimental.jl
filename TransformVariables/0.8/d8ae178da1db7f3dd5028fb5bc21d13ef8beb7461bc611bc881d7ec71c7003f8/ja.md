```julia
value_and_logjac_forwarddiff(
    f,
    x;
    flatten,
    handleNaN,
    chunk,
    cfg
)

```

`f`の`x`における値と対数ヤコビ行列式を計算します。`flatten`は、`f`を全単射にする結果からベクトルを取得するために使用されます。
