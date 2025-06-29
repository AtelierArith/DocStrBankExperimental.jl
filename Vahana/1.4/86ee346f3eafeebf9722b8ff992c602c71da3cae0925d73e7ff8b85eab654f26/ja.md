```
register_edgetype!(types::ModelTypes, ::Type{T}, [hints...; kwargs...])
```

`types`に追加のエッジタイプを登録します。

エッジタイプ T は、[`Edge{T}`](@ref) の状態（フィールド）を定義する構造体です。これらの構造体は「ビットタイプ」でなければならず、すなわち、タイプは不変であり、原始的なタイプと他のビットタイプのみを含む必要があります。これらのタイプ T はしばしば無状態であり、その場合、モデルの既存のエッジタイプを区別するためのタグとして使用されます。

メモリ内のグラフを格納するために使用される内部データ構造は、ヒントパラメータによって変更できます：

  * `:IgnoreFrom`: ソースエージェントのIDは保存されません。これは、エッジのソースにあるエージェントの状態が、例えば[`neighborstates`](@ref)関数を介してアクセスできないことを意味します。
  * `:Stateless`: ソースエージェントのIDのみを保存します。
  * `:SingleType`: すべてのターゲットエージェントが同じタイプである必要があり、キーワード`target`も必要です（下記参照）。
  * `:SingleEdge`: 各エージェントは最大1つのエッジのターゲットになれます。
  * `:IgnoreSourceState`: このIDを持つエージェントの状態にアクセスするためにソースエージェントのIDは使用されません。
  * `:NumEdgesOnly`: `:IgnoreFrom`と`:Stateless`を組み合わせます。
  * `:HasEdgeOnly`: `:IgnoreFrom`、`:Stateless`、および`:SingleEdge`を組み合わせます。

`:SingleType`が設定されている場合、キーワード引数`target`を追加する必要があります。この引数の値はターゲットノードのタイプでなければなりません。`target`キーワードが存在するが、`:SingleType`ヒントが明示的に指定されていない場合、暗黙的に設定されます。

このタイプのエージェントがいくつ存在するかがわかっている場合、オプションの`size`キーワードを介して指定することもできます。これによりパフォーマンスが向上する可能性がありますが、メモリ使用量が増加する可能性もあります。

`register_edgetype!`のパイプ可能なバージョンも利用可能で、`register_*`呼び出しのシーケンスを介してモデルを構築できます。このパイプラインは`ModelTypes()`をソースとして開始し、[`create_model`](@ref)関数を宛先として終了します。

詳細については、[Edge Hints](./performance.md#Edge-Hints)、[`add_edge!`](@ref)、および[`add_edges!`](@ref)を参照してください。
