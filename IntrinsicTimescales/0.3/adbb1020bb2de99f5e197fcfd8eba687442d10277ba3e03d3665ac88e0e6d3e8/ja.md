```
IntrinsicTimescales
```

時系列データからのタイムスケール推定のためのJuliaパッケージ。

# 機能

  * INT計算のための標準技術: ACW-50, ACW-0, FOOOF
  * パラメータ推定のための近似ベイズ計算 (ABC)
  * 変分推論のためのADVI
  * 複数のモデルタイプ:

      * 単一タイムスケール
      * 振動を伴う単一タイムスケール
      * 欠損データをサポートするモデル
  * 周期グラム、Welch (DSP.jlから) およびLomb-Scargle (LombScargle.jlから) を使用した要約統計量:

      * 自己相関関数 (ACF)
      * パワースペクトル密度 (PSD)

# サブモジュール

  * `Models`: 抽象モデルタイプとインターフェース
  * `ABC`: 近似ベイズ計算アルゴリズム
  * `TuringBackend`: ADVIのためのTuring.jl統合
  * `SummaryStats`: ACFおよびPSDの実装
  * `Distances`: ABCのための距離メトリック
  * `Utils`: 分析のためのユーティリティ関数
  * `OrnsteinUhlenbeck`: DifferentialEquations.jlを使用したOUプロセス生成
  * `OneTimescale`: 単一タイムスケールモデル
  * `OneTimescaleAndOsc`: 振動を伴う単一タイムスケール
  * `OneTimescaleWithMissing`: 欠損データを伴う単一タイムスケール
  * `OneTimescaleAndOscWithMissing`: 欠損データを伴う単一タイムスケールと振動
  * `Plotting`: 結果のためのプロット関数
