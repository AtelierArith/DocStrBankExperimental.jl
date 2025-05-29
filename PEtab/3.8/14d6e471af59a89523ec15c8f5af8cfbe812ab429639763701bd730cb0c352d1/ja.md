```
Fides(hessian_method; verbose::Bool=false)
```

パラメータ推定のためのボックス制約付きニュートン・トラスト領域最適化器[Fides](https://github.com/fides-dev/fides)をセットアップします。

[`calibrate`](@ref)および[`calibrate_multistart`](@ref)も参照してください。

## 引数

  * `hessian_method`: ヘッセ行列を計算するための方法。許可されるオプションは次のとおりです：

      * `nothing`: `PEtabODEProblem`によって計算されたヘッセ行列が使用されます。
      * `:BB`: ブロイデンの「悪い」方法。
      * `:BFGS`: ブロイデン-フレッチャー-ゴールドファーブ-シャノン更新戦略。
      * `:BG`: ブロイデンの「良い」方法。
      * `:Broyden`: ブロイデン類の更新スキーム。
      * `:SR1`: 対称ランク1更新。
      * `:SSM`: 構造化セカント法。
      * `:TSSM`: 完全構造化セカント法。
  * `verbose`: パラメータ推定中に進行状況を印刷するかどうか。

## 説明

Fidesはボックス制約付き最適化問題のためのニュートン・トラスト領域最適化器です。アルゴリズムに関する詳細は[1]にあります。Fidesは、完全なヘッセ行列を計算するのが計算上高価すぎる場合に特に優れていますが、ガウス-ニュートンヘッセ行列の近似を計算することができます（詳細についてはドキュメントを参照してください）。`PEtabODEProblem`を介してユーザーのヘッセ行列をサポートするだけでなく、いくつかのヘッセ行列近似方法もサポートしています。上記よりも詳細な説明については、Fidesの[ドキュメント](https://github.com/fides-dev/fides)を参照してください。

1. Fröhlich and Sorger, PLoS computational biology, pp e1010322 (2022)
