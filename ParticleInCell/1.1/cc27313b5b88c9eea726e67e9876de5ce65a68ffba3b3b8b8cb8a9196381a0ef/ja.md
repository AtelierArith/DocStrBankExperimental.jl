すべてのグリッドオブジェクトの親タイプであり、シミュレーションドメインを定義し、座標系間の変換を行うために使用されます。シミュレーションドメイン内の位置を参照できる3つの異なる番号付けシステムがあります。

1. 点の「物理座標」は、その点に関連付けられた実際の（次元を持つ）座標です。この値は、シミュレーションの下限から上限までの範囲になります。この値は通常、`Vector{T}`または`NTuple{N, T}`の形式を取り、`T <: Real`です。
2. 点の「セル座標」は、セルの長さの単位での点の非次元的な位置です。この値は0からnum_cells - 1までの範囲、またはガードセルが含まれる場合はこの範囲外になります。この値は通常、`NTuple{N, Int}`または`NTuple{N, T}`の型を持ち、`T <: Real`です。
3. 点の「セルインデックス」は、その点でフィールド配列にインデックスを付けるために使用できる`CartesianIndex`です。この値は厳密に`axes(field.values)`に制限されなければならず、任意の次元に対して通常は1からnum*cells + 2*num*guard_cells + 1までの範囲になります。

最初の2つのインデックス付けタイプ、phys*coordsとcell*coordsは、特定のフィールド内のガードセルの数に依存せず、グリッド量のみに依存します。したがって、これらのシステム間の変換に必要なユーティリティは、グリッドオブジェクトへの参照のみを必要とします。一方、cell_indexのユーティリティは使用されるフィールドに特有であり、したがって座標変換を行うためには`AbstractField`を提供する必要があります。

一般的に、物理座標は粒子の位置を考慮する際に便利であり、セルインデックスは粒子の位置への補間に使用されます。セル座標は、特に非一様グリッドのために定義された補間アルゴリズムに便利です。
