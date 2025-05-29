```
evaluate(tf, z)
```

`TransferFunction`である`tf`を特定の数値`z`（複素数である可能性があります）で評価します。

# 例

```jldoctest eval
tf = TransferFunction([1], [3, 1])
evaluate(tf, 1.0)
# 出力
0.25
```
