```
FeaturizeGroupAcrossParameter <: GlobalContinuationAlgorithm
FeaturizeGroupAcrossParameter(mapper::AttractorsViaFeaturizing; kwargs...)
```

[`global_continuation`](@ref) のためのメソッドです。これは [`AttractorsViaFeaturizing`](@ref) で議論された特徴化アプローチを使用しており、そのため入力としてそのマッパーのインスタンスが必要です。 [`global_continuation`](@ref) で使用されると、特徴が抽出され、パラメータ範囲にわたってグループ化されます。言い換えれば、すべての初期条件のすべての特徴がすべてのパラメータ値にわたって同じ「プール」に入れられ、その後マッパーの `group_config` に従ってグループ化されます。グループ化が完了すると、特徴ラベルの割合がそれらが来た各パラメータ値に分配されます。

この継続法は、[Gelbrecht2020](@cite) および [Stender2021](@cite) の論文のアプローチに基づいていますが、強く一般化されています。

## キーワード引数

  * `info_extraction::Function` クラスタに対応する特徴ベクトルのベクトルを入力として受け取り、クラスタの説明を返す関数です。デフォルトでは、クラスタの重心が使用されます。これは、`global_continuation` の返り値に含まれる `attractors_cont` に含まれています。
