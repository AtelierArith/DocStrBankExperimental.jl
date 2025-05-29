```
strategy_returns(
    objs::Vector{<:FinancialInstrument},
    pricing_model,
    strategy_type,
    future_prices,
    n_timesteps,
    timesteps_per_period,
    cash_injection = 0.0,
    fin_obj_count,
    widget_count,
    pay_int_rate = 0.0,
    hold_return_int_rate = 0.0;
    kwargs...
)
```

複数の金融商品に対して、与えられた金利と価格で取引またはヘッジ戦略をテストするためのシミュレーション環境。取引戦略を定義するための新しいメソッドを `strategy()` 関数に提供することで使用されます。

戦略からのドル累積リターン、戦略のすべての保有の時系列、および更新されたオブジェクト配列を返します。

## 引数

  * `objs::Vector{<:FinancialInstrument}`: 取引またはヘッジ戦略が実行される金融商品のベクター
  * `pricing_model`: `obj` の価格を定義する `Model` サブタイプ
  * `strategy_type`: `strategy()` 関数がディスパッチされる `Hedging` サブタイプ。新しい `strategy()` メソッドのために新しいサブタイプを提供する必要があります
  * `future_prices`: `objs` の金融商品で使用される基礎となる `Widget` 資産の将来の価格のベクターの辞書

注: 辞書のキーは各基礎資産の `widget.name` フィールド文字列でなければなりません

  * `n_timesteps`: 戦略をテストするためのタイムステップの数
  * `timesteps_per_period`: データ内のタイムステップのサイズに対して、特定の期間のタイムステップの数、負であってはなりません。たとえば、関心のある期間が1年で、日次株データが使用される場合、`timesteps_per_period=252` となります。正でなければなりません。
  * `cash_injection`: 戦略を開始する際に所有する現金の量
  * `fin_obj_count`: 戦略を開始する際に所有する金融商品の量の辞書

注: 辞書のキーは各金融商品の `FinancialInstrument.label` フィールド文字列でなければなりません

  * `widget_count`: 戦略を開始する際に所有する金融商品で使用される基礎資産の量の辞書

注: 辞書のキーは各基礎資産の `Widget.name` フィールド文字列でなければなりません

  * `pay_int_rate`: 負の現金残高に対して支払われる連続金利
  * `hold_return_int_rate`: 正の現金残高に対して得られる連続金利
  * `kwargs`: `price!()` または `strategy()` 関数に必要なキーワード引数を通過させる

## 例

```
# 使用するウィジェットと金融商品を作成
stock = Stock(; prices=[99, 97, 90, 83, 83, 88, 88, 89, 97, 100], name="stock", timesteps_per_period=252)
stock2 = Stock(; prices=[66, 61, 70, 55, 65, 63, 57, 55, 53, 68], name="stock2", timesteps_per_period=252)
call = EuroCallOption(stock, 110; maturity=.5, label="call", risk_free_rate=.02)
call2 = EuroCallOption(stock2, 70; maturity=1, label="call2", risk_free_rate=.02)
objs = [call, call2]

# 各ウィジェットの将来の価格のための辞書を作成
future_prices = Dict(
    "stock" => [100, 104, 109, 105, 108, 108, 101, 101, 104, 110],
    "stock2" => [67, 74, 73, 67, 67, 75, 69, 71, 69, 70]
)

# 各ウィジェットと金融商品の開始時の保有量のための辞書を作成
fin_obj_count = Dict("call" => 1.0, "call2" => 2)
widget_count = Dict("stock" => 2.0, "stock2" => 3)
cash_injection = 0.0

pay_int_rate = 0.08
hold_return_int_rate = 0.02

cumulative_return, ts_holdings, obj_array = strategy_returns(
    objs, 
    BlackScholes,
    Naked,
    future_prices,
    10,
    252,
    cash_injection,
    fin_obj_count,
    widget_count, 
    pay_int_rate, 
    hold_return_int_rate
)
```
