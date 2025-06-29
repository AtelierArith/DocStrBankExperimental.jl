```julia
struct RayBasis2D{T1, T2, T3<:(AbstractVector), T4, T5} <: DataDrivenAcoustics.DataDrivenPropagationModel{T1}
```

2D平面波RBNNの定式化。

  * `env`: データ駆動型の水中環境
  * `calculatefield`: 音響場を推定するための関数（デフォルト: `RayBasis2DCal`）
  * `nrays`: 光線の数（デフォルト: 60）
  * `θ`: 到達光線の方位角（ラジアン）（デフォルト: 欠損）
  * `A`: 到達光線の振幅（デフォルト: 欠損）
  * `ϕ`: 光線の位相（ラジアン）（デフォルト: 欠損）
  * `k`: 角周波数（rad/m）（デフォルト: 欠損）
  * `trainable`: 学習可能なパラメータ（デフォルト: 空）
  * `ini_lr`: 初期学習率（デフォルト: 0.001）
  * `trainloss`: 学習およびモデル更新に使用される損失関数（デフォルト: `rmseloss`）
  * `dataloss`: 早期停止のためのベンチマーク検証エラーを計算するデータ損失関数（デフォルト: `rmseloss`）
  * `ratioₜ`: データ分割比率 = 学習データの数/(学習データの数 + 検証データの数)（デフォルト: 0.7）
  * `seed`を`true`に設定してランダムデータ選択順序をシードする（デフォルト: `false`）
  * `maxepoch`: 許可される最大学習エポック数（デフォルト: 10000000）
  * `ncount`: 学習率を減少させる前の最大試行回数（デフォルト: 5000）
  * 学習率が`minlearnrate`より小さくなるとモデルの学習が終了する（デフォルト: 1e-6）
  * `ncount`に達すると学習率は`reducedlearnrate`によって減少する（デフォルト: 10）
  * `showloss`をtrueに設定すると、モデルの学習プロセス中に検証エラーが歴史的に最良である場合、学習および検証エラーを表示する（デフォルト: `false`）
