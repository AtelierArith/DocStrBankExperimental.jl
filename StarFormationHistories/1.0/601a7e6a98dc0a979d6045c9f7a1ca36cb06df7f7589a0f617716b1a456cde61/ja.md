```
LinearAMR(constraint1, constraint2, T_max::Real=137//10,
          free::NTuple{2, Bool}=(true, true))
```

MH制約から2つの異なるルックバック時間で`LinearAMR`のインスタンスを構築します。`constraint1`と`constraint2`はそれぞれ長さ2のインデクサブル（例えば、タプル）であり、最初の要素は金属量 [M/H] で、2番目の要素はGyr単位のルックバック時間です。制約の順序は重要ではありません。

# 例

```jldoctest; setup = :(import StarFormationHistories: LinearAMR)
julia> LinearAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) isa LinearAMR{Float64}
true

julia> LinearAMR((-2.5, 13.7), (-1.0, 0.0), 13.7) == LinearAMR((-1.0, 0.0), (-2.5, 13.7), 13.7)
true
```
