```
KeyRateZero(timepoint,shift=0.001) <: KeyRateDuration
```

指定された時点で指定された量だけパラメータ曲線をシフトします。`duration`と組み合わせて使用して、キー レート デュレーションを計算します。

他のデュレーション統計が解析的導関数を使用して計算されるのに対し、`KeyRateDuration`はシフトおよび計算によるイールドカーブアプローチを介して計算されます。

`KeyRateZero`は、固定収入市場では（[`KeyRatePar`](@ref)よりも）あまり一般的に報告されていませんが、後者はより解析的に魅力的な特性を持っています。FinanceModels.jl ドキュメントの KeyRateDuration に関する議論を参照してください。
