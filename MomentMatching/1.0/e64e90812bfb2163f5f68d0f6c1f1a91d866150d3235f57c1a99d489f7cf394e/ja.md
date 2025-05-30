```julia
struct EstimationResult{S<:AbstractFloat, T<:Integer, U<:MomentMatching.AuxiliaryParameters, V<:MomentMatching.PredrawnShocks}
```

# 説明

モーメント推定手続きの出力を格納するための構造体。

# フィールド

  * `npmm`: 数値パラメータ
  * `aux`: 補助入力
  * `presh`: 事前に描かれたショック
  * `xlocstart`: 開始パラメータ - ローカルステージのみが実行される場合に関連
  * `pmm`: モーメント推定入力
  * `fglo`: グローバルステージにおける目的関数の値、昇順にソート
  * `xglo`: グローバルステージでチェックされたパラメータの組み合わせ、目的関数の値に従ってソート
  * `momglo`: モデルからのモーメント、グローバルステージ
  * `floc`: ローカルステージにおける目的関数の値、昇順にソート
  * `xloc`: ローカルステージでチェックされたパラメータの組み合わせ、目的関数の値に従ってソート
  * `momloc`: モデルからのモーメント、ローカルステージ
  * `conv`: 論理値、真の場合はローカルステージで最小値における収束基準が満たされていることを示す
