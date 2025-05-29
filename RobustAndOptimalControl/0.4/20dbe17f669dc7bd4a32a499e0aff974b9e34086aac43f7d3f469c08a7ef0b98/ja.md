```
controller_reduction(P::ExtendedStateSpace, K, r, out=true; kwargs...)
```

最小化    ||(K-Kᵣ) W||∞ もし out=false             ||W (K-Kᵣ)||∞ もし out=true 参照: Robust and Optimal Control Ch 19.1 out は重みが出力重みまたは入力重みとして適用されるかどうかを示します。

この関数は*正のフィードバックコントローラ `K` を期待します。

このメソッドは、Andreas Varga の "Controller Reduction Using Accuracy-Enhancing Methods" における SW1/SW2(SPA) とラベル付けされたメソッドに対応しています。SW1 はデフォルトのメソッドで、`out=true` に対応します。

このメソッドは不安定なコントローラをサポートしていません。代替手段については上記の参考文献を参照してください。また、[`stab_unstab`](@ref) および [`baltrunc_unstab`](@ref) も参照してください。
