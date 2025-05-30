```
StatsAPI.fit(::Type{<:PowerTransformation}, y::AbstractVector{<:Number}; atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
            maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, X::AbstractMatrix{<:Number},
             y::AbstractVector{<:Number}; atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, formula::FormulaTerm, data;
             atol=1e-8,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
StatsAPI.fit(::Type{<:PowerTransformation}, model::LinearMixedModel;
             atol=1e-8, progress=true,
             algorithm::Symbol=:LN_BOBYQA, opt_atol=1e-8, opt_rtol=1e-8,
             maxiter=-1)
```

データのパワー変換に対する最適なλ値を見つけます。

`X`が提供されない場合、`y`は無条件分布として扱われます。

`X`が提供されると、`y`は`X`によって定義された線形予測子に条件付けられた分布として扱われます。各反復ステップで、`X`をモデル行列として用いて変換された`y`に単純線形回帰が適合されます。

`FormulaTerm`が提供される場合、`X`はその仕様と`data`を使用して構築されます。

`LinearMixedModel`が提供される場合、`X`と`y`はモデルオブジェクトから抽出されます。

!!! note
    フォーミュラインターフェースは、StatsModels.jlが直接またはGLM.jlやMixedModels.jlなどの他のパッケージを介してロードされている場合にのみ利用可能です。


!!! note
      * フォーミュラインターフェースはパッケージ拡張として定義されています。
      * MixedModelsインターフェースはパッケージ拡張として定義されています。


`atol`は、`λ`をゼロとして扱うための絶対許容誤差を制御します。

`opt_`キーワード引数は、NLoptに渡される許容誤差です。

`maxiter`は最適化に使用する最大反復回数を指定します。負の値は制限を設けません。

`algorithm`は最適化に使用する有効なNLoptアルゴリズムです。

`progress`は最適化プロセス中の中間モデルフィットのためのプログレスバーを有効にします。
