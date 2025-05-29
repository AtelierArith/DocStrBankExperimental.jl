```
RequireMarginalFunctionalDependencies(specifications::NamedTuple)
RequireMarginalFunctionalDependencies(; specifications...)
```

`DefaultFunctionalDependencies`と同様ですが、エッジからメッセージを計算するためには、このエッジの周辺も必要です。

仕様パラメータは、エッジの名前とその初期周辺を含む名前付きタプルです。名前付きタプルに名前が存在する場合、それは同じエッジの外向きメッセージの計算がこのエッジの周辺を使用する必要があることを示します。名前付きタプルに`nothing`が値として渡されると、初期周辺は設定されません。この構文では、`NamedTuple`を直接使用する代わりに、コンストラクタにキーワード引数を渡すことができます。

```julia
RequireMarginalFunctionalDependencies(μ = vague(NormalMeanPrecision),     τ = nothing)
                                     # ^^^                               ^^^
                                     # 'x'のために'marginal'を要求      'τ'についても同様にできますが、
                                     # `vague(...)`で初期化します      ここでは初期化をスキップします
```

関連情報: [`ReactiveMP.DefaultFunctionalDependencies`](@ref), [`ReactiveMP.RequireMessageFunctionalDependencies`](@ref), [`ReactiveMP.RequireEverythingFunctionalDependencies`](@ref)
