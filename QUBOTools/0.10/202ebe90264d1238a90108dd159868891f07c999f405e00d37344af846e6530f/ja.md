```
reads(model)
reads(solution::AbstractSolution)
```

各サンプルからの合計リード数を返します。

```
reads(model, i::Integer)
reads(solution::AbstractSolution, i::Integer)
```

利用可能な場合、モデルの現在の解における$i$-番目のサンプルのサンプリング周波数を返します。
