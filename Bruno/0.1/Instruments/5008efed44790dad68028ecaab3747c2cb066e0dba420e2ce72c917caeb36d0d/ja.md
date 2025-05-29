```
Bond(prices, name, time_mat, coupon_rate)
Bond(price; kwargs...)
Bond(;kwargs)
```

金融商品の基礎資産として使用するためのBond型を構築します。

## 引数

  * `prices`: 歴史的価格（1次元配列として入力）または現在の価格を数値 `<: Real` として入力します。
  * `name`: 債券または発行会社の文字列名。デフォルトは ""。
  * `time_mat`: 債券が満期になるまでの時間（年単位）。デフォルトは1。
  * `coupon_rate`: 債券のクーポンレート。デフォルトは .03。

## 例

```julia
Bond([1,2,3,4,5], "Example", .5, .05)

kwargs = Dict(:prices => [1, 2, 3, 4, 5], :name => "Example", :time_mat => .5, :coupon_rate => .05);
Bond(;kwargs...)

Bond(2; coupon_rate=.05)
```
