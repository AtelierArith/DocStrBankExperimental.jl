```
absvec(q)
```

クォータニオンの「ベクトル」成分の二乗の合計の平方根。

この関数は、オーバーフローとアンダーフローを回避するために、Juliaの組み込み`hypot`関数を使用します。

# 例

```jldoctest
julia> absvec(quaternion(1,2,3,6))
7.0
```
