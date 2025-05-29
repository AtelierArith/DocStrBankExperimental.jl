```
price!(fin_obj<:CallOption, pricing_model::Type{<:Model};kwargs...)
```

与えられた金融オブジェクトの価値を計算します。

# 構文

```
price!(fin_obj, PricingModelType; kwargs...)
```

キーワード引数は、Pricing Model Type によって異なります。

# 例

```julia
# 基本資産を作成
a_stock = Stock(41; volatility=.3)

# ヨーロピアンコールオプションを作成
a_fin_inst = EuroCallOption(a_stock, 40; risk_free_rate=.05) 

# オプションの価値辞書に二項木のコール値を追加
price!(a_fin_inst, BinomialTree)  
```
