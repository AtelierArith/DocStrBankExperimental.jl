```
    mutable struct Parameters{PPHY <: AbstractEmptyParams, PSIM <: AbstractEmptyParams, PHY <: AbstractEmptyParams,
                    PSOL <: AbstractEmptyParams, PUDE <: AbstractEmptyParams, PINV <: AbstractEmptyParams}
```

シミュレーションまたはモデルのさまざまなパラメータセットを保持する可変構造体です。

# フィールド

  * `physical::PPHY`: 物理パラメータ。
  * `simulation::PSIM`: シミュレーションパラメータ。
  * `hyper::PHY`: ハイパーパラメータ。
  * `solver::PSOL`: ソルバーパラメータ。
  * `UDE::PUDE`: ユニバーサル微分方程式（UDE）パラメータ。
  * `inversion::PINV`: 逆行列パラメータ。

# 型パラメータ

  * `PPHY`: 物理パラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
  * `PSIM`: シミュレーションパラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
  * `PHY`: ハイパーパラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
  * `PSOL`: ソルバーパラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
  * `PUDE`: UDEパラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
  * `PINV`: 逆行列パラメータの型で、`AbstractEmptyParams`のサブタイプでなければなりません。
