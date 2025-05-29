```
predict(mm::LinearModel, newx::AbstractMatrix;
        interval::Union{Symbol,Nothing} = nothing, level::Real = 0.95)
```

`interval`が`nothing`（デフォルト）の場合、モデル`mm`と新しいデータ`newx`に対する予測値のベクトルを返します。それ以外の場合、予測値のベクトルと、指定された`level`（0.95はalpha = 0.05に相当）に対する下限および上限の信頼区間のベクトルを返します。`interval`の有効な値は、予測された関係の不確実性を区切る`:confidence`と、新しいデータポイントの推定範囲を区切る`:prediction`です。
