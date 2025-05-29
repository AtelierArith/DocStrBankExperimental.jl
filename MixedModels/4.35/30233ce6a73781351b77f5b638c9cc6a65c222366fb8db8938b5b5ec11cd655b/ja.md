```
OptSummary
```

最適化の概要

# フィールド

## 許容値、初期値と最終値

  * `initial`: 最適化における初期パラメータ値のコピー
  * `finitial`: 目的関数の初期値
  * `lowerbd`: パラメータ値の下限
  * `final`: 最適化からの最終パラメータ値のコピー
  * `fmin`: 目的関数の最終値
  * `feval`: 関数評価の回数 利用可能なバックエンドは `OPTIMIZATION_BACKENDS` を介して確認できます。
  * `returnvalue`: 戻り値、`Symbol` として。利用可能な戻り値はバックエンドによって異なります。
  * `xtol_zero_abs`: 実質的にゼロと見なされる近ゼロパラメータの許容値
  * `ftol_zero_abs`: 近ゼロパラメータをゼロに設定するための目的関数の変化に対する許容値
  * `maxfeval`: NLopt (`maxeval`) および PRIMA (`maxfun`) と同様

## 最適化手法とバックエンドの選択

  * `optimizer`: 使用される最適化手法の名前、`Symbol` として
  * `backend`: 最適化手法を提供する最適化ライブラリ、デフォルトは `NLoptBackend`。

## バックエンド固有のフィールド

  * `ftol_rel`: NLopt と同様、PRIMA では使用されない
  * `ftol_abs`: NLopt と同様、PRIMA では使用されない
  * `xtol_rel`: NLopt と同様、PRIMA では使用されない
  * `xtol_abs`: NLopt と同様、PRIMA では使用されない
  * `initial_step`: NLopt と同様、PRIMA では使用されない
  * `maxtime`: NLopt と同様、PRIMA では使用されない
  * `rhobeg`: PRIMA と同様、NLopt では使用されない
  * `rhoend`: PRIMA と同様、NLopt では使用されない

## MixedModels 固有のフィールド、最適化手法とは無関係

  * `fitlog`: 最適化のステップからのパラメータと目的値のタプルのベクトル
  * `nAGQ`: GLMM の逸脱評価における適応ガウス-エルミート積分点の数
  * `REML`: LMM フィットのために REML 基準を使用
  * `sigma`: LMM の残差標準偏差の事前値

!!! note
    `fitlog` 内のパラメータ値の内部ストレージは、将来的に各スナップショットのために異なる `AbstractVector` のサブタイプ（例: `StaticArrays.SVector`）を使用するように変更される可能性がありますが、これは破壊的変更とは見なされません。


!!! note
    フィールドの正確な順序と数は、追加のバックエンドやその機能のサポートが追加されるにつれて変更される可能性があります。言い換えれば: キーワードコンストラクタを使用し、**位置引数コンストラクタ**は使用しないでください。

