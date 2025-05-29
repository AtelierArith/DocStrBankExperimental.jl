```julia
struct DesignDistribution
```

  * `factors::NamedTuple`
  * `formula::StatsModels.FormulaTerm`

1つ以上の`Distribution`をカプセル化し、ランダムデザインを生成します。*Distributions*パッケージから`Distribution`に関連付けられた因子名の`NamedTuple`を受け取ります。`DesignDistribution`をインスタンス化した後は、[`rand`](@ref)を使用してサンプルを要求する必要があり、これにより[`RandomDesign`](@ref)が生成されます。
