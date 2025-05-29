```
evaluate(A::AbstractTensorTrain, X...)
```

テンソル列 `A` を入力 `X` で評価します。

例:

```@example
    L = 3
    q = (2, 3)
    A = rand_tt(4, L, q...)
    X = [[rand(1:qi) for qi in q] for l in 1:L]
    evaluate(A, X)
```
