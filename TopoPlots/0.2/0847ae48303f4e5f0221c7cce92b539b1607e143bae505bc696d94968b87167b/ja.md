```
NaturalNeighboursMethod(; method=Sibson(1), kwargs...)
```

データを補間するために、[NaturalNeighbours.jl](https://github.com/DanielVandH/NaturalNeighbours.jl) パッケージを使用する補間器です。これは、データを補間するためにデローニ三角形分割と対応するボロノイ図を使用し、`Sibson(::Int)`、`Nearest()`、`Triangle()`などのさまざまな方法を提供します。

ボロノイ図に基づく方法の利点は、不規則に分布したデータセットやいくつかの不連続性に対してより堅牢であることです。これにより、一部の多項式ベースの方法や独立した距離加重（クリギング）が影響を受ける可能性があります。NaturalNeighboursがクールである理由についての詳細は、[このDiscourseの投稿](https://discourse.julialang.org/t/ann-naturalneighbours-jl-natural-neighbour-interpolation-and-derivative-generation/99164/11)を参照してください。

メソッドに簡単にアクセスするには、`using NearestNeighbours`を実行してください。

詳細については、[NaturalNeighboursのドキュメント](https://github.com/DanielVandH/NaturalNeighbours.jl)を参照してください。

このメソッドは完全に構成可能で、すべての引数を関連するNaturalNeighbours.jlの関数に転送します。メソッドが何をするかを理解するには、[`NaturalNeighbours.jl`](https://github.com/DanielVandH/NaturalNeighbours.jl)のドキュメントを参照してください。

## キーワード引数

ここで注目すべき主なキーワード引数は`method`で、補間に使用する方法です。他のキーワード引数は単にNaturalNeighbours.jlの補間器に転送されます。

  * `method`: 補間に使用する方法。デフォルトは`Sibson(1)`です。デフォルト: NaturalNeighbours.Sibson{1}()
  * `parallel`: 補間時にマルチスレッドを使用するかどうか。デフォルトは`true`です。デフォルト: true
  * `project`: データをデローニ三角形分割に投影するかどうか。デフォルトは`true`です。デフォルト: true
  * `derivative_method`: 微分に使用する方法。デフォルトは`Direct()`です。`Direct()`または`Iterative()`のいずれかです。デフォルト: NaturalNeighbours.Direct()
  * `use_cubic_terms`: 二次導関数を推定するために三次項を使用するかどうか。`derivative_method == Direct()`の場合のみ関連します。デフォルト: true
  * `alpha`: 二次導関数を推定するために使用される重み付けパラメータ。`derivative_method == Iterative()`の場合のみ関連します。デフォルト: 0.1
