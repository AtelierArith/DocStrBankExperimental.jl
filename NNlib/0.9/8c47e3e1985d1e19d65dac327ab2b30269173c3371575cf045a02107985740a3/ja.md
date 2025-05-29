```
bias_act!(σ, x, b)
```

これは `x .= σ.(x .+ b)` と同等であり、`sigmoid` と `tanh` を `sigmoid_fast` と `tanh_fast` に置き換えます。`x` が `StridedArray{<:AbstractFloat}` の場合のみ、`x` を上書きします。

勾配内で使用される場合、`σ` が入力を全く必要としない `derivatives_given_output` のメソッドを持つときのみ上書きされます。そのようなメソッドは、例えば `@scalar_rule relu(x) Ω > 0` によって定義され、導関数は `Ω`（出力）のみを含み、`x` は含まれません。

!!! warning
    `x` が他の関数の勾配にまだ必要な場合は、安全に使用することはできません。誤った使用は静かに間違った答えを返します。これは主にFluxレイヤーのために意図されており、前の操作が安全であることが知られている場合、例えば `bias_act!(σ, weight * input, bias)` のように `Dense` レイヤーで使用されます。

