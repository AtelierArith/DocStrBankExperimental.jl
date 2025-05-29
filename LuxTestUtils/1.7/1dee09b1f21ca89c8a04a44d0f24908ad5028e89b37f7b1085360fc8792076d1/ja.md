```
test_gradients(f, args...; skip_backends=[], broken_backends=[], kwargs...)
```

`f`の`args`に関する勾配を指定されたバックエンドを使用してテストします。

| バックエンド         | ADType              | CPU | GPU | メモ          |
|:-------------- |:------------------- |:--- |:--- |:----------- |
| Zygote.jl      | `AutoZygote()`      | ✔   | ✔   |             |
| Tracker.jl     | `AutoTracker()`     | ✔   | ✔   |             |
| ReverseDiff.jl | `AutoReverseDiff()` | ✔   | ✖   |             |
| ForwardDiff.jl | `AutoForwardDiff()` | ✔   | ✖   | `len ≤ 100` |
| FiniteDiff.jl  | `AutoFiniteDiff()`  | ✔   | ✖   | `len ≤ 100` |
| Enzyme.jl      | `AutoEnzyme()`      | ✔   | ✖   | リバースモードのみ   |

## 引数

  * `f`: 勾配をテストする関数。
  * `args`: 勾配をテストする引数。勾配計算には`AbstractArray`のみが考慮されます。他の引数に関する勾配は`NoTangent()`であると仮定されます。

## キーワード引数

  * `skip_backends`: スキップするバックエンドのリスト。
  * `broken_backends`: 壊れていると見なすバックエンドのリスト。
  * `soft_fail`: `true`の場合、テストは`soft_fail`テストとして記録されます。これは任意の`broken`キーワード引数を上書きします。代わりに、`soft_fail`にバックエンドのリストを渡すことで、特定のバックエンドのみのsoft_failテストを許可できます。
  * `enzyme_set_runtime_activity`: `true`の場合、Enzymeのランタイムアクティビティを有効にします。
  * `enable_enzyme_reverse_mode`: `true`の場合、Enzymeのリバースモードを有効にします。
  * `kwargs`: `check_approx`に渡す追加のキーワード引数。

## 例

```julia
julia> f(x, y, z) = x .+ sum(abs2, y.t) + sum(y.x.z)

julia> x = (; t=rand(10), x=(z=[2.0],))

julia> test_gradients(f, 1.0, x, nothing)

```
