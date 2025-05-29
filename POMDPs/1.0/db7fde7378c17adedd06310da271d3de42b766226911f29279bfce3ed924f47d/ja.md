```
gen(m::Union{MDP,POMDP}, s, a, rng::AbstractRNG)
```

MDP/POMDP生成モデル全体を実装するための関数で、`NamedTuple`を返します。

`gen`は、次の状態、観測、および報酬の*2つ以上*を同時に生成する必要がある場合に*のみ*実装されるべきです。状態遷移モデルが報酬および観測モデルから分離できる場合は、`gen`の代わりに`ImplicitDistribution`を使用して`transition`を実装するべきです。

ソルバーおよびシミュレーターの作成者は、生成モデルを呼び出すために`@gen`マクロを使用するべきです。

# 引数

  * `m`: `MDP`または`POMDP`モデル
  * `s`: 現在の状態
  * `a`: アクション
  * `rng`: 擬似乱数生成器（通常は`MersenneTwister`）

# 戻り値

関数は[`NamedTuple`](https://docs.julialang.org/en/v1/base/base/#Core.NamedTuple)を返すべきです。以下のエントリのサブセットを含みます：

## MDP

  * `sp`: 次の状態
  * `r`: ステップの報酬
  * `info`: 追加のデバッグ情報、通常はNamedTupleのような連想コンテナに格納されます

## POMDP

  * `sp`: 次の状態
  * `o`: 観測
  * `r`: ステップの報酬
  * `info`: 追加のデバッグ情報、通常はNamedTupleのような連想コンテナに格納されます

いくつかの要素は省略可能です。たとえば、`o`が戻り値から省略された場合、問題作成者は`observation`を実装することもでき、POMDPs.jlは必要に応じて自動的にそれを使用します。

# 例

```julia
struct LQRMDP <: MDP{Float64, Float64} end

POMDPs.gen(m::LQRMDP, s, a, rng) = (sp = s + a + randn(rng), r = -s^2 - a^2)
```
