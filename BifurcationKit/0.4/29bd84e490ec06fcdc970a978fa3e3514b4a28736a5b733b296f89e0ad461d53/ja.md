```julia
struct ContinuousEvent{Tcb, Tl, T, Tf, Td} <: BifurcationKit.AbstractContinuousEvent
```

継続アルゴリズムにContinuousEvent関数を渡すための構造体。連続コールバックは**タプル/スカラー**値を返し、そのゼロを求めます。

  * `nb::Int64`: イベントの数、すなわちコールバック関数が返す結果の長さ
  * `condition::Any`: `(iter, state) -> NTuple{nb, T}` コールバック関数で、各継続状態でタプルを返します。例えば、1.0および-2.0での交差を検出するには、`(iter, state) -> (getp(state)+2, getx(state)[1]-1)`を渡すことができます。型`T`は、`continuation`の`::Lens`で指定されたパラメータの型と一致する必要があります。
  * `computeEigenElements::Bool`: イベントが固有要素を計算する必要があるかどうか
  * `labels::Any`: 情報を表示するために使用されるラベル。例えば、`labels[1]`はタイプ`(0, 1.3213, 3.434)`のイベントを特定するために使用されます。`labels = ("hopf",)`または`labels = ("hopf", "fold")`を使用できます。`labels::Union{Nothing, NTuple{N, String}}`である必要があります。
  * `tol::Any`: 真のイベントとして宣言するためのイベント値の許容誤差。
  * `finaliser::Any`: ファイナライザ関数
  * `data::Any`: 一部の個人データを保存する場所
