```
setfc(model, fc)
```

モデル内のすべての変数の最終条件のベクトルを返します。すべての変数の最終条件は `fc` に設定されますが、ショックと外生変数は常に `fcnone` です。個々の変数の最終条件を更新するには [`setfc!`](@ref) を使用してください。
