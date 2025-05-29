```
build_quadratic_cost_matrix(linear_sys, ssys::ODESystem, costs::Vector{Pair})
```

線形化されたシステムに対して、簡略化されたシステム `ssys` の状態または出力にペナルティを課す二次コスト行列（LQRまたはカルマンフィルタリング用）を組み立てます。このペナルティは、ペアのベクトル `costs` に従います。

この関数の動機は、ModelingToolkitが保証しないことです。

  * 簡略化後にどの状態が状態として選択されるか。
  * 状態の順序。

上記の2番目の問題、状態の順序は `reorder_states` を使用して回避できますが、最初の問題は単純な再順序付けでは解決できません。この関数は、ユーザーが選択した状態実現のコストの配列を受け入れ、MTKによって選択された状態実現のための正しいコスト行列を組み立てます。これを行うために、関数は線形化（`linear_sys`）と簡略化されたシステムの両方が必要です。これらは [`linearize`](@ref) の出力です。

# 引数:

  * `linear_sys`: [`linearize`](@ref) の出力で、`C` というプロパティを持つオブジェクトです。これは [`ControlSystemsBase.StateSpace`](@ref) または `C` フィールドを持つ `NamedTuple` である可能性があります。
  * `ssys`: [`linearize`](@ref) の出力です。
  * `costs`: ペアのベクトルです。

```
