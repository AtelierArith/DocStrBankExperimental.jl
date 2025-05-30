```
update_suffstats!(m::AbstractDPM, data, i::Int, k::Int, l::Int)
```

`i` 番目のクラスタラベルが `k` から `l` に変更された後、データセット `data` を考慮して `m` の十分統計量を更新します。
