```
ExpandTable(scale, freq) => Array{Int64, 1}
expandtable(scale, frea) => Array{Int64, 1}
```

頻度表から生のスコア配列を展開します。

# 引数

  * `scale` 生のスコアスケールを表す実数のベクトル。
  * `freq` カウントされた頻度を含む整数のベクトル。

# 例

```julia
sc = [0, 1, 2, 3]
fq = [10, 3, 15, 4]
ExpandTable(sc, fq)
```
