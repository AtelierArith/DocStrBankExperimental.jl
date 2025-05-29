```
set_mu_s_kagome(sim::AtomisticSim, Ms::Number)
```

与えられた原子システム `sim` のカゴメ格子に対して、磁気モーメント `mu_s` を設定します。

### 使用例

```julia
set_mu_s_kagome(sim, 2 * mu_B)
```

これは、カゴメ格子のすべてのサイトに対して磁気モーメントを `2 * mu_B` に設定します。    
