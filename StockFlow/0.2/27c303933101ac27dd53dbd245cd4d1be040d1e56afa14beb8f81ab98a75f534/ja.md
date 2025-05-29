CausalLoop（名前付き頂点のグラフ）を頂点のベクトルと頂点のペアのベクトルで作成します。

CausalLoop([:A, :B], [:A => :B, :B => :B]) は、頂点 A と B を持ち、エッジ A => B とエッジ B => B を持つ CausalLoop を作成します。
