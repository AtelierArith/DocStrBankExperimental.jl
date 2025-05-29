# RPTreeArg

ツリー成長のための引数を収集します

FIELDS

  * D : すべての距離を計算するために使用するメトリック
  * depth : ツリーの最大深さ
  * threshold : ノード内の2つのオブジェクト間の距離の平均（meanD）と最大（maxD）との比率。

    そして、分割する際の最大直径（maxDiameter）と2つのオブジェクト間の平均距離。 maxD / meanD > threshold の場合、ノード内の球面性を達成するために直径で分割します。 そうでなければ、投影によって分割します。 したがって、threshold = 1 の場合、常に直径による分割ルールを使用し、threshold が高いほど、投影ルールによる分割ノードが増えます。

    関数 analyzeSplittingInfo は、実行後の分割に関する情報を取得し、得られた情報に応じて threshold を調整するために使用できます。

CONSTRUCTORS

RPTreeArg(D::Distances.SemiMetric, depth::Int64, thresh::Float64)
