```
resampler = Resampler(
    model=ConstantRegressor(),
    resampling=CV(),
    measure=nothing,
    weights=nothing,
    class_weights=nothing
    operation=predict,
    repeats = 1,
    acceleration=default_resource(),
    check_measure=true,
    per_observation=true,
    logger=default_logger(),
    compact=false,
)
```

*プライベートメソッド。自己責任で使用してください。*

`TunedModel` インスタンスおよび `IteratedModel` インスタンスの `fit` メソッドによって内部的に使用されるリサンプリングモデルラッパー。オプションの意味については [`evaluate!`](@ref) を参照してください。一般ユーザーが使用することを意図しておらず、通常は [`evaluate!`](@ref) を直接使用します。

マシン `mach = machine(resampler, args...)` が与えられた場合、指定された `model` のパフォーマンス評価が、処方された `resampling` 戦略およびその他のパラメータに従って、データ `args...` を使用して行われます。これは `fit!(mach)` の後に `evaluate(mach)` を呼び出すことで実行されます。

その後の `fit!(mach)` の呼び出しでは、`resampling`、`repeats`、または `cache` フィールドの `resampler` が変更されない限り、新しいトレイン/テストペアの行インデックスは再生成されません。`resampler` の RNG フィールドの進化は *変更* を構成しません（`MLJType` オブジェクトの `==` はそのような変更に敏感ではありません; [`is_same_except`](@ref) を参照してください）。

単一のトレイン/テストペアがある場合、ラップされたモデル `resampler.model` のウォームリスタート動作は、ラッパー `resampler` のウォームリスタート動作に拡張され、ラップされたモデルの変異に関して適用されます。

サンプル `weights` は、評価のために重みをサポートする指定されたパフォーマンス測定に渡されます。これらの重みは、ラップされた `model` のトレーニングに使用されるマシン内の `Resampler` インスタンスにバインドされた重みと混同しないでください。

サンプル `class_weights` は、評価のためにクラスごとの重みをサポートする指定されたパフォーマンス測定に渡されます。これらの重みは、ラップされた `model` のトレーニングに使用されるマシン内の `Resampler` インスタンスにバインドされた重みと混同しないでください。
