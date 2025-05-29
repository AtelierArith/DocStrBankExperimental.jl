```
interactive_poincaresos_scan(A::StateSpaceSet, j::Int; kwargs...)
interactive_poincaresos_scan(As::Vector{StateSpaceSet}, j::Int; kwargs...)
```

`A`のポアンカレ断面を「脳スキャン」のようにスキャンするためのインタラクティブなアプリケーションを起動します。断面を定義する平面はスライダーを介して任意に移動できます。`figure, ax3D, ax2D`を返します。

入力データセットは3次元でなければならず、ここで交差平面は常にデータセットの`j`-番目の変数が事前に定義された値を越えるときに選択されます。スライダーは自動的に`j`-番目の変数が取得できるすべての可能な値を取得します。

複数のデータセットが与えられた場合、キーワード`colors`はそれぞれに色を割り当てます。例えば、`colors = [JULIADYNAMICS_COLORS[mod1(i, 6)] for i in 1:length(As)]`のようにします。

キーワード`linekw, scatterkw`は名前付きタプルであり、それぞれ線と散布図にキーワード引数として伝播されます。一方、キーワード`direction = -1`は関数`DyamicalSystems.poincaresos`に伝播されます。
