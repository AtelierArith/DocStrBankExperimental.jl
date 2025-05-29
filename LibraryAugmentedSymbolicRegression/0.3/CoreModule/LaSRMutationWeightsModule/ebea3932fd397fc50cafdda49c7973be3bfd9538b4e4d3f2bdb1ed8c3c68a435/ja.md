```
LaSRMutationWeights <: AbstractMutationWeights
```

LaSRモジュール内のすべての突然変異操作のための複合重みを定義します。 [`MutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.MutationWeights)で定義された突然変異重みに加えて、この構造体にはLLM突然変異操作の重みも含まれています。これらのLLM重みは手動で設定することもできますし、llm*operation*weightsに基づいてプログラム的に設定することもできます。重みは合計が1.0になるように正規化されています。

# 参照

  * [`AbstractMutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.AbstractMutationWeights): カスタム突然変異重みタイプを定義するために使用します。
  * [`MutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.MutationWeights): SRモジュールのデフォルトの突然変異重みです。
