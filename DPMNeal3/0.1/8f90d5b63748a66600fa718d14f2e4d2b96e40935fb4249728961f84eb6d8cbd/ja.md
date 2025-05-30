```
update_suffstats!(m::AbstractDPM, data, i::Int, k::Int, l::Int)
```

`data`の与えられたデータセットに対して、`i`番目のクラスタラベルが`k`から`l`に変更された後に、`m`内の十分統計量を更新します。
