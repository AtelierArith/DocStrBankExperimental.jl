```
controller_reduction_plot(G, K)
```

正規化コプライムマージン（[`ncfmargin`](@ref)）を、コントローラの順序の関数としてプロットします。コントローラを削減するために[`baltrunc_coprime`](@ref)が使用されるとき、赤、オレンジ、緑の帯は、それぞれ悪い、まあまあ、良いコプライム不確実性マージンの目安に対応します。値が0の場合は、不安定な閉ループを示します。

`G`がExtendedStateSpaceシステムである場合、コントローラを削減するために[`controller_reduction`](@ref)が使用されるとき、入力と性能出力の間の$H_∞$ノルム$||T_{zw}||_\infty$を示す2番目のプロットが表示されます。

正規化コプライムマージンが十分に大きい限り、コントローラの順序は安全に削減できます。コントローラにインテグレータが含まれている場合、削減からインテグレータを保護することが推奨されることがあります。たとえば、コントローラが[`glover_mcfarlane`](@ref)を使用して取得された場合、`K`ではなく`info.Gs, info.Ks`で削減を行い、削減された`Ks`を使用して`Kr`を形成します。

例については、[`glover_mcfarlane`](@ref)または[ドキュメント](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Example-of-controller-reduction:)を参照してください。
