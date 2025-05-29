```
@sampler(def)
```

StochasticProgramsと互換性のある`scenariotype`のためのサンプラータイプを次の構文を使用して定義します。

```julia
@sampler samplername = begin
    ...internals...

    @sample scenariotype begin
        ...
        return scenario
    end
end
```

サンプラーに必要な内部状態や特別なコンストラクタは、他のJulia構造体と同様に@samplerブロック内で定義されます。サンプル操作は[`@sample`](@ref)ブロック内で定義し、サンプラーが返す`scenariotype`を指定します。定義されたサンプラーはすべてのJuliaプロセスで利用可能です。

## 例

以下は、[`@scenario`](@ref)で定義されたシナリオのための内部重み値を持つシンプルなダミーサンプラーを定義し、1つのシナリオをサンプリングします。

```jldoctest; setup = :(@scenario ExampleScenario = ξ::Float64), filter = r".*"
@sampler ExampleSampler = begin
    w::Float64

    ExampleSampler(w::AbstractFloat) = new(w)

    @sample ExampleScenario begin
        @parameters w
        return ExampleScenario(w*randn(), probability = rand())
    end
end
s = ExampleSampler(2.0)
s()

# output

ExampleScenario with probability 0.29
  ξ: 1.48


```

参照: [`@sample`](@ref), [`@scenario`](@ref)
