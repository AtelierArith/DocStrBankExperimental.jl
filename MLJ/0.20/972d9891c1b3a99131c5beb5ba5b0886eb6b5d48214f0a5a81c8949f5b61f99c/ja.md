MLJ

[`MLJ`](https://juliaai.github.io/MLJ.jl//dev/)は、Juliaのための機械学習ツールボックスです。以下にリストされた別々のコンポーネントからの機能を集約しており、個別にロードすることができます。

実際のモデルコード（例：`DecisionTreeClassifier`のインスタンス化のためのコード）は、モデル提供パッケージから明示的にロードする必要があります。例えば、`@load`を使用します。ただし、コアモデルラッパーやいくつかの一般的なトランスフォーマーはすぐに利用可能です。起動時に`localmodels(wrappers=true)`を実行してリストを表示します。

# コンポーネント

  * MLJBase.jl: `machine`インターフェース、データセットを`partition`および`unpack`するためのツール、モデルのパフォーマンスのための`evaluate`/`evaluate!`、`|>`パイプライン構文、`TransformedTargetModel`ラッパー、一般的なモデル構成構文（学習ネットワーク）、合成データ生成器、MLJがデータをどのように解釈するかを確認するための`scitype`および`schema`メソッド（ScientificTypes.jlから）。一般的に、MLJワークフローには必要です。
  * StatisticalMeasures.jl: 機械学習のためのMLJ互換の測定（メトリクス）、混同行列、ROC曲線。
  * MLJModels.jl: データ前処理のための一般的なトランスフォーマー、モデルレジストリの検索、`@load`を使用したモデルのロード。
  * MLJTuning.jl: `TunedModel`ラッパーを介したハイパーパラメータ最適化。
  * MLJIteration.jl: 繰り返しモデルを制御するための`IteratedModel`ラッパー。
  * MLJEnsembles.jl: `EnsembleModel`ラッパーを介した同質モデルのアンサンブル。
  * MLJBalancing.jl: パイプライン内でのオーバーサンプリング/アンダーサンプリング手法の組み込み、`BalancedModel`ラッパーを介して。
  * FeatureSelection.jl: 特徴選択のためのトランスフォーマー、および監視モデルラッパー`RecursiveFeatureSelection`。
  * MLJFlow.jl: MLflowワークフロートラッキングとの統合。
  * OpenML.jl: OpenML.orgからデータセットを取得するためのツール。
