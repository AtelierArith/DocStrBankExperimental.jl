```
strategy_returns(
    obj::FinancialInstrument,
    pricing_model,
    strategy_type,
    future_prices,
    n_timesteps,
    timesteps_per_period,
    cash_injection = 0.0,
    fin_obj_count = 0.0,
    widget_count = 0.0,
    pay_int_rate = 0.0,
    hold_return_int_rate = 0.0;
    kwargs...
)
```

与えられた金利と価格に対して取引またはヘッジ戦略をテストするためのシミュレーション環境。取引戦略を定義する新しいメソッドを `strategy()` 関数に提供することで使用されます。

戦略からのドル累積リターン、戦略のすべての保有の時系列、および更新されたオブジェクト配列を返します。

## 引数

  * `obj`: 取引またはヘッジ戦略が実行される金融商品
  * `pricing_model`: `obj` の価格を定義する `Model` サブタイプ
  * `strategy_type`: `strategy()` 関数がディスパッチされる `Hedging` サブタイプ。新しい `strategy()` メソッドのために新しいサブタイプを提供する必要があります
  * `future_prices`: 戦略を実行するための基礎となる `Widget` 資産の将来の価格のベクトル
  * `n_timesteps`: 戦略をテストするためのタイムステップの数
  * `timesteps_per_period`: データ内のタイムステップのサイズに対して、特定の期間のタイムステップの数。負の値にはできません。たとえば、関心のある期間が1年で、日次株データが使用される場合、`timesteps_per_period=252`。正である必要があります。
  * `cash_injection`: 戦略を開始する際に所有する現金の量
  * `fin_obj_count`: 戦略を開始する際に所有する金融商品の量
  * `widget_count`: 戦略を開始する際に所有する基礎となる `Widget` の量
  * `pay_int_rate`: 負の現金残高に対して支払われる連続金利
  * `hold_return_int_rate`: 正の現金残高に対して得られる連続金利
  * `kwargs`: `price!()` または `strategy()` 関数に必要なキーワード引数を通過させる

## 例

```
# 使用するための Widget と FinancialInstrument を作成
stock = Stock(; prices=[99, 97, 90, 83, 83, 88, 88, 89, 97, 100], name="stock", timesteps_per_period=252)
call = EuroCallOption(stock, 110; maturity=.5, label="call", risk_free_rate=.02)

# future_prices 配列を作成
future_prices = [100, 104, 109, 105, 108, 108, 101, 101, 104, 110]

fin_obj_count = 2
widget_count = 3
pay_int_rate = .05
hold_return_int_rate = .02

cumulative_return, ts_holdings, obj = strategy_returns(
    call, 
    BlackScholes,
    Naked,
    future_prices,
    10,
    252, 
    10.0, 
    fin_obj_count, 
    widget_count,
    pay_int_rate, 
    hold_return_int_rate;
    transaction_cost = 0.0
)
```
