グラフにおける頂点の隣接点。

グラフにおいて、この関数は[`outneighbors`](@ref)のエイリアスです。対称グラフでは、頂点は同じ出辺と入辺を持つため、区別は無意味です。

複数の辺が存在する場合、隣接する頂点は*重複を含めて*与えられます。ユニークな隣接点を取得するには、`unique(neighbors(g))`を呼び出してください。
