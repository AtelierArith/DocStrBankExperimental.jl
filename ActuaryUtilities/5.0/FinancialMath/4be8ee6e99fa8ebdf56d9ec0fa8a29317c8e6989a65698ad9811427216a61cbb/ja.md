```
KeyRatePar(timepoint,shift=0.001) <: KeyRateDuration
```

指定された時点で指定された量だけパラメータ曲線をシフトします。`duration`と組み合わせて、キー レート デュレーションを計算します。

他のデュレーション統計が解析的導関数を使用して計算されるのに対し、`KeyRateDuration`はシフト アンド コンピュートのイールド カーブ アプローチを介して計算されます。

`KeyRatePar`は、後者がより解析的に魅力的な特性を持っているにもかかわらず、固定収入市場で（[`KeyRateZero`](@ref)よりも）一般的に報告されます。FinanceModels.jl ドキュメントでの KeyRateDuration の議論を参照してください。
