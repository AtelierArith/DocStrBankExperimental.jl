```
compress(A::SparseTensor)
```

重複したインデックスを `A` で圧縮します。

# 例

```julia
using ADCME
indices = [
    1 1 
    1 1
    2 2
    3 3
]
v = [1.0;1.0;1.0;1.0]
A = SparseTensor(indices[:,1], indices[:,2], v, 3, 3)
Ac = compress(A)
sess = Session(); init(sess)

run(sess, A.o.indices) # 期待される出力: [0 0;0 0;1 1;2 2]
run(sess, A.o.values) # 期待される出力: [1.0;1.0;1.0;1.0]


run(sess, Ac.o.indices) # 期待される出力: [0 0;1 1;2 2]
run(sess, Ac.o.values) # 期待される出力: [2.0;1.0;1.0]
```

!!! note
    `A` のインデックスはソートされている必要があります。`compress` は入力引数の有効性をチェックしません。

