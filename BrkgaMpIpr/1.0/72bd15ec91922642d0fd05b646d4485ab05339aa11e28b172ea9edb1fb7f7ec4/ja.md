```
affect_solution_hamming_distance(block1::SubArray{Float64, 1},
                                 block2::SubArray{Float64, 1},
                                 threshold::Float64 = 0.5)::Bool
```

`block1`のキーのブロックを`block2`のキーのブロックに変更することが解決策に影響を与える場合、[ハミング距離](https://en.wikipedia.org/wiki/Hamming_distance)に基づいて`true`を返します。

!!! note
    この関数は、しきい値/直接染色体表現により適している可能性があります。


!!! note
    `block1`と`block2`は同じサイズでなければなりません。パフォーマンスの理由から境界チェックは行われません。


!!! note
    この関数は、パフォーマンスの理由から`@inline`で注釈されています。


# 引数

  * `block1::SubArray{Float64, 1}`: 最初のベクトル。
  * `block2::SubArray{Float64, 1}`: 2番目のベクトル。
  * `threshold::Float64 = 0.5`: 二値化のためのしきい値。
