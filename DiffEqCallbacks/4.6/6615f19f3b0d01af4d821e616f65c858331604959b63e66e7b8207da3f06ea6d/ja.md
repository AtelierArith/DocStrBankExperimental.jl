```julia
IterativeCallback(time_choice, user_affect!, tType = Float64;
    initial_affect = false, kwargs...)
```

いくつかの影響を反復的に適用するために使用されるコールバックです。たとえば、`t₁`で最初の効果が与えられた場合、次の効果を適用するために`t₂`を定義できます。

## 引数

  * `time_choice(integrator)`は次のコールバックの時間を決定します。時間の選択に対して`nothing`が返されると、イテレータは終了します。
  * `user_affect!`は停止点で積分器に適用される効果です。

## キーワード引数

  * `initial_affect`は`t=0`で効果を適用するかどうかで、デフォルトは`false`です。
