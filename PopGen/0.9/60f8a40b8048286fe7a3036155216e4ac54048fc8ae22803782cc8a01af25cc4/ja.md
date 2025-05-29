```
pairwisefst(data::PopData; method::Function, by::String = "global", iterations::Int64)
```

`PopData`オブジェクト内の集団間のペアワイズFSTを計算します。`iterations`を`0`より大きい値に設定すると、統計的有意性のP値を得るための片側の置換検定を実行します。`by = "locus"`を使用すると、集団ペアのローカスごとのFSTを計算します（反復と有意性検定は無視されます）。`PairwiseFST`オブジェクトを返し、推定値を得るために使用された`method`とともに`results`の`DataFrame`を格納します。

#### 方法:

  * `AMOVA`: Bird et al. (2011) によって説明されたAMOVAベースの (Excoffier, 1992) FST（デフォルト）
  * `Hudson`: Hudson et al. (1992) メソッド（バイアレリックデータのみ）
  * `Nei`: Nei (1987) メソッド
  * `WeirCockerham` : Weir & Cockerham (1984) メソッド

**例**

```julia
data = @nancycats
wc = pairwise_fst(data, method = WeirCockerham)
wc_sig = pairwise_fst(data, iterations = 1000)
```
