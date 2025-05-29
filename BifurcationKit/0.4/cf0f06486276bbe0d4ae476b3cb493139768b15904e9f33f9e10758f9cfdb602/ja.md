```julia
struct DiscreteEvent{Tcb, Tl, Tf, Td} <: BifurcationKit.AbstractDiscreteEvent
```

離散イベント関数を継続アルゴリズムに渡すための構造体。離散コールバックは離散値を返し、私たちはそれが変化する時を探します。

  * `nb::Int64`: イベントの数、すなわちコールバック関数によって返される結果の長さ
  * `condition::Any`: = `(iter, state) -> NTuple{nb, Int64}` 各継続状態でタプルを返すコールバック関数。例えば、値の変化を検出するために使用します。
  * `computeEigenElements::Bool`: イベントが固有要素を計算する必要があるかどうか
  * `labels::Any`: 情報を表示するために使用されるラベル。例えば `labels[1]` は最初のコンポーネントで発生するイベントを特定するために使用されます。`labels = ("hopf",)` または `labels = ("hopf", "fold")` を使用できます。`labels::Union{Nothing, NTuple{N, String}}` を持つ必要があります。
  * `finaliser::Any`: ファイナライザ関数
  * `data::Any`: 一部の個人データを保存する場所
