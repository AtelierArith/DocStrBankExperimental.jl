```
bhar(
    data::FixedTable{T, 2};
    minobs=0.8
) where {T}

bhar(
    data::FixedTable,
    rr::RegressionModel;
    minobs=0.8
)

bhar(
    data::IterateFixedTable{T, 2};
    minobs=0.8
) where {T, MNames, FNames}

bhar(
    data::IterateFixedTable,
    rrs::AbstractVector{<:BasicReg};
    minobs=0.8
)
```

企業とベンチマークの間のバイ・アンド・ホールドリターン（幾何学的リターンとも呼ばれる）の差を計算します。回帰が渡されると、ベンチマークはその回帰からの係数と回帰内のベンチマークのパフォーマンスに基づいています。これらは時々ファマ・フレンチの異常リターンと呼ばれます。回帰が渡されない場合、異常リターンはFixedTableの最初の列と2番目の列の差として計算されます（2番目の列は通常、S&P 500やすべての企業の時価総額加重リターンなどのベンチマークです）。

回帰を構築するのと同様に、`IterateFixedTable`を渡すとベクターが返され、より最適化された方法が使用されます。
