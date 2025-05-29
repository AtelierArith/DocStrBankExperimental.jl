```
Scheduler{T, F} <: Optimiser.AbstractRule
Scheduler(constructor, schedules::AbstractSchedule...)
Scheduler(constructor; field_a = schedule_a, field_b = schedule_b, ...)
```

1つ以上のスケジュールとオプティマイザを`Scheduler`でラップします。[`Optimisers.apply!`](https://fluxml.ai/Optimisers.jl/dev/api/#Optimisers.apply!)が呼び出されるたびに、スケジュールが反復され、`constructor`が更新されたパラメータで最適化ルールを呼び出すために使用されます。`Scheduler`は、Optimisers.jlのオプティマイザが使用される場所であればどこでも使用できます。

単一のスケジュールとオプティマイザルールが渡された場合、スケジューラは学習率`opt.eta`を更新します。複数のハイパーパラメータを調整するには、複数のスケジュールを引数またはキーワードとして渡します。これらは順番に反復され、`constructor`に渡されます（つまり、`constructor`は適切な数の引数/キーワードを受け入れる必要があります）。

# 引数

  * `constructor`: いくつかのパラメータを与えて最適化ルールを作成するコンストラクタ（例: `Optimisers.AdamW`；`()`がないことに注意）
  * `schedules`: 複数の（名前付き）引数としてスケジュールする最適化ルールのハイパーパラメータのリスト

# 例

```julia
# Descentのためのコサインアニーリングスケジュール
julia> opt = Scheduler(Descent, CosAnneal(l0 = 0.1, l1 = 0.8, period = 10));

# Momentumの学習率とモーメンタムをスケジュール
julia> opt = Scheduler(Momentum, CosAnneal(l0 = 0.1, l1 = 0.8, period = 10), Exp(0.999, 0.8));

# カスタム固定学習率でAdamWの重み減衰項をスケジュール
julia> opt = Scheduler(AdamW, eta = 1e-4, decay = Exp(1e-3, 0.7));
```
