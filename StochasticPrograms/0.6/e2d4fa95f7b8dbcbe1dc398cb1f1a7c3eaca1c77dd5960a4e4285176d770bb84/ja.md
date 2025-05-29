```
@stochastic_model(def)
```

確率モデルを定義し、確率プログラムをインスタンス化できるようにします。構文は次の通りです。

```julia
@stochastic_model model_name begin
    ...
    @stage x begin
      ...
    end
    ...
end
```

ここで、内側のブロックは [`@stage`](@ref) ブロックです。少なくとも2つのステージを連続して指定する必要があります。確率モデルオブジェクトは、後で与えられたシナリオのセットを使用するか、サンプラーを使用して確率プログラムを [`instantiate`](@ref) するために使用できます。モデルは [`@stage`](@ref) ブロック内で `model_name` を使用して参照されます。`model_name` を省略すると、マクロは匿名モデルオブジェクトを返し、予約語 `model` を [`@stage`](@ref) ブロック内で使用する必要があります。そうでない場合、結果の確率モデルオブジェクトは `model_name` という名前の変数に格納されます。

## 例

以下は、次のような最初のステージモデルからなる確率モデルを定義します。

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

および次のような第二ステージモデル：

$$
  minimize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

ここで、$q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$ はシナリオ $ξ$ に依存します。

```julia
@stochastic_model sm begin
    @stage 1 begin
        @decision(sm, x₁ >= 40)
        @decision(sm, x₂ >= 20)
        @objective(sm, Min, 100*x₁ + 150*x₂)
        @constraint(sm, x₁ + x₂ <= 120)
    end
    @stage 2 begin
        @uncertain q₁ q₂ d₁ d₂
        @variable(sm, 0 <= y₁ <= d₁)
        @variable(sm, 0 <= y₂ <= d₂)
        @objective(sm, Min, q₁*y₁ + q₂*y₂)
        @constraint(sm, 6*y₁ + 10*y₂ <= 60*x₁)
        @constraint(sm, 8*y₁ + 5*y₂ <= 80*x₂)
    end
end
```

または、匿名構文を使用して次のように記述できます。

```julia
sm = @stochastic_model begin
    @stage 1 begin
        @decision(model, x₁ >= 40)
        @decision(model, x₂ >= 20)
        @objective(model, Min, 100*x₁ + 150*x₂)
        @constraint(model, x₁ + x₂ <= 120)
    end
    @stage 2 begin
        @uncertain q₁ q₂ d₁ d₂
        @variable(model, 0 <= y₁ <= d₁)
        @variable(model, 0 <= y₂ <= d₂)
        @objective(model, Min, q₁*y₁ + q₂*y₂)
        @constraint(model, 6*y₁ + 10*y₂ <= 60*x₁)
        @constraint(model, 8*y₁ + 5*y₂ <= 80*x₂)
    end
end
```

ここで、予約語 `model` が全体で使用されています。

参照： [`@stage`](@ref), [`@parameters`](@ref), [`@decision`](@ref), [`@uncertain`](@ref)
