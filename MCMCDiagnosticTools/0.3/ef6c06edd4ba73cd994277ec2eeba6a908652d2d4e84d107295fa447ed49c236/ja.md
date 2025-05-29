```
rstar(
    rng::Random.AbstractRNG=Random.default_rng(),
    classifier,
    samples,
    chain_indices::AbstractVector{Int};
    subset::Real=0.7,
    split_chains::Int=2,
    verbosity::Int=0,
)
```

テーブル`samples`の$R^*$収束統計量を`classifier`で計算します。

`samples`は、行がサンプルで列がパラメータである`AbstractMatrix`、`AbstractVector`、またはテーブル（すなわち、Tables.jlインターフェースを実装している）でなければなりません。

`chain_indices`は、`samples`の各行のチェーンIDを示します。

このメソッドは、長さが異なるチェーン、すなわち不均一なチェーンをサポートしています。
