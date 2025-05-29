```
affect_solution_kendall_tau(block1::SubArray{Float64, 1},
                            block2::SubArray{Float64, 1})::Bool
```

`block1`のキーのブロックを`block2`のキーのブロックに変更すると、[Kendall Tau距離](https://en.wikipedia.org/wiki/Kendall_tau_distance)に基づいて解に影響を与える場合は`true`を返します。

!!! note
    `block1`と`block2`は同じサイズでなければなりません。パフォーマンス上の理由から境界チェックは行われません。


# 引数

  * `block1::SubArray{Float64, 1}`: 最初のベクトル。
  * `block2::SubArray{Float64, 1}`: 2番目のベクトル。
