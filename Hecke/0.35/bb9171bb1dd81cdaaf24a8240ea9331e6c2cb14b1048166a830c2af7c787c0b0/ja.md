```
saturate(A::ZZMatrix) -> ZZMatrix
```

行列 $A$ の飽和を計算します。すなわち、$\mathbf{Q}\otimes M \cap \mathbf{Z}^n$ の基底を求めます。ここで、$M$ は $A$ の行スパンであり、$n$ は $A$ の列数です。

同等に、$TA$（ゼロ行を除く）を返します。ここで、$T$ は $TA$ が整数であり、$TA$ の基本因子がすべて自明であるような可逆有理行列です。

# 例

```jldoctest
julia> saturate(ZZ[1 2 3;4 5 6;7 0 7])
[1    2    3]
[1    1    1]
[0   -1   -1]

julia> saturate(ZZ[1 2 3;4 5 6;7 8 9])
[1   2   3]
[1   1   1]

julia> saturate(ZZ[1 2 3;4 5 6])
[1   2   3]
[1   1   1]

julia> saturate(ZZ[1 2;3 4;5 6])
[1   2]
[1   1]

```
