`CalcFactor`の因子をサンプリングします。デフォルトの`getSample`メソッドが提供されており、ほとんどの使用ケースをカバーするはずですが、より高度なサンプリングが必要な場合は、`getSample`関数を拡張する必要があります。

`getSample`のデフォルトの動作は次のとおりです：

  * `SamplableBelief`はフィールド`Z`にあり、これだけで因子を完全に定義するのに十分である必要があります。すなわち、`Z<:SamplableBelief`が唯一のフィールドであるべきです。
  * グループ多様体上で定義された`<:AbstractManifoldMinimize`因子のサンプリング：

      * `getSample`は通常、単位元での接ベクトルを返しますが、カスタム因子定義に一致する必要があります。
  * 事前の`<:AbstractPrior`因子のサンプリング：

      * `getSample`は、変数の点表現に一致する多様体上の点を返さなければなりません。

注意事項

  * ユーザーは、因子が`SamplableBelief`のためにフィールド`Z`だけを使用しない場合、このメソッドをオーバーロードする必要があります。
  * より多くの例と詳細については、Caesar.jlのドキュメントのカスタム因子セクションを参照してください。
  * また、問題https://github.com/JuliaRobotics/IncrementalInference.jl/issues/1441も参照してください。

参照：[`getMeasurementParametric`](@ref)
