```
optimize_index!(
    index::AbstractSearchIndex,
    context::AbstractContext,
    kind::ErrorFunction=MinRecall(0.9);
    space::AbstractSolutionSpace=optimization_space(index),
    context_exhaustive_search=GenericContext(context),
    queries=nothing,
    ksearch=10,
    numqueries=64,
    initialpopulation=16,
    maxpopulation=16,
    bsize=4,
    mutbsize=16,
    crossbsize=8,
    tol=-1.0,
    maxiters=16,
    verbose=false,
    params=SearchParams(; maxpopulation, bsize, mutbsize, crossbsize, tol, maxiters, verbose)
)
```

`index`を指定されたパフォーマンス（`kind`）を達成するように構成しようとします。最適化手順は、`kind`と`queries`によって得られる構成空間に対する確率的探索です。

# 引数

  * `index`: 最適化されるインデックス
  * `context`: インデックスコンテキスト
  * `kind`: 適用する最適化の種類。`ParetoRecall()`、`ParetoRadius()`、または`MinRecall(r)`（ここで`r`は期待されるリコール（0-1、1が最高品質だが検索時間がかかる））のいずれかです。

# キーワード引数

  * `space`: 探索空間を定義します
  * `queries`: パフォーマンスを測定するために使用されるクエリのセット、検証セット。`AbstractDatabase`または何も指定しないことができます。
  * `queries_ksearch`: `queries`のために取得する隣接点の数
  * `queries_size`: `queries===nothing`の場合、すでにインデックスされたデータベースのサンプルが使用され、`queries_size`はサンプルのサイズです。
  * `initialpopulation`: 最適化手順の初期サンプル
  * `minbatch`: 構成を評価するためにマルチスレッドがどのように使用されるかを制御します。[`getminbatch`](@ref)を参照してください。
  * `params`: ソルバーのパラメータ。詳細については、[`SearchParams` arguments of `SearchModels.jl`](https://github.com/sadit/SearchModels.jl)パッケージを参照してください。代わりに、いくつかのキーワード引数を`SearchParams`に渡し、残りのデフォルト値を使用することができます：

      * `initialpopulation=16`: 初期サンプル
      * `minbatch=0`: 最小バッチサイズ（`Polyester`マルチスレッド、`0`は入力に基づいてサイズを選択します）
      * `maxpopulation=16`: 人口の上限
      * `bsize=4`: ビームサイズ（選択、突然変異、交差操作で使用される最良の要素）
      * `mutbsize=16`: 各イテレーションでの突然変異した新しい要素の数
      * `crossbsize=8`: 交差操作からの新しい要素の数
      * `maxiters=16`: 最大イテレーション数
      * `verbose`: 手順が冗長かどうかを制御します
