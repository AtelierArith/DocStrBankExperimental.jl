```
NLLSsolver.printoutcallback(cost, problem, data, iteratedata)
```

各最適化イテレーションでコスト、コストの変化、ステップサイズを出力するコールバック。

# 例

次のようにNLLSsolver問題を最適化すると：

```julia
    NLLSsolver.optimize!(problem, options, unfixed, printoutcallback)
```

イテレーションごとの情報がターミナルに出力されます。

!!! note
    このコールバックはデバッグに役立ちますが、パフォーマンスにペナルティが発生します。

