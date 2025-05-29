```
RequireMessageFunctionalDependencies(specifications::NamedTuple)
RequireMessageFunctionalDependencies(; specifications...)
```

`DefaultFunctionalDependencies`と同様ですが、エッジからメッセージを計算するためには、このエッジのインバウンドメッセージも必要です。

仕様パラメータは、エッジの名前とその初期メッセージを含む名前付きタプルです。名前付きタプルに名前が存在する場合、それは同じエッジのアウトバウンドメッセージの計算がインバウンドメッセージを使用する必要があることを示します。名前付きタプルに`nothing`が値として渡されると、初期メッセージは設定されません。この構文では、`NamedTuple`を直接使用する代わりに、コンストラクタにキーワード引数を渡すことができます。

```julia
RequireMessageFunctionalDependencies(μ = vague(NormalMeanPrecision),     τ = nothing)
                                     # ^^^                               ^^^
                                     # 'x'のために'inbound'を要求       'τ'についても同様にできますが、
                                     # `vague(...)`で初期化します      ここでは初期化をスキップします
```

関連情報: [`ReactiveMP.DefaultFunctionalDependencies`](@ref), [`ReactiveMP.RequireMarginalFunctionalDependencies`](@ref), [`ReactiveMP.RequireEverythingFunctionalDependencies`](@ref)
