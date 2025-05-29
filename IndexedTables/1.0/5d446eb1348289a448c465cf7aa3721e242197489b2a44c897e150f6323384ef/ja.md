```
groupreduce(f, t, by = pkeynames(t); select)
```

テーブル `t` のグループに対して、選択 `by` の値で定義されたグループに対して `f` の [`reduce`](@ref) 操作を計算します。結果はユニークな `by` 値でキー付けされたテーブルに格納されます。

# 例

```
t = table([1,1,1,2,2,2], 1:6, names=[:x, :y])
groupreduce(+,        t, :x; select = :y)
groupreduce((sum=+,), t, :x; select = :y)  # 出力列名を :sum に変更

t2 = table([1,1,1,2,2,2], [1,1,2,2,3,3], 1:6, names = [:x, :y, :z])
groupreduce(+, t2, (:x, :y), select = :z)

# 異なる列に対する異なるリデューサ
groupreduce((sumy = :y => +, sumz = :z => +), t2, :x)
```
