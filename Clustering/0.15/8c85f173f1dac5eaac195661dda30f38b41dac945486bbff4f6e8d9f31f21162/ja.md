```
affinityprop(S::AbstractMatrix; [maxiter=200], [tol=1e-6], [damp=0.5],
             [display=:none]) -> AffinityPropResult
```

類似度行列 `S` に基づいてアフィニティ伝播クラスタリングを実行します。

$$
S_{ij}
$$

($i ≠ j$) は $i$ 番目と $j$ 番目の点の間の類似度（または負の距離）であり、$S_{ii}$ は $i$ 番目の点の *エグゼンプラ* としての *可用性* を定義します。

# 引数

  * `damp::Real`: 減衰係数、$0 ≤ \mathrm{damp} < 1$。大きな値は、より遅い（おそらくより安定した）更新を示します。$\mathrm{damp} = 0$ は減衰を無効にします。
  * `maxiter`, `tol`, `display`: [共通オプション](@ref common_options)を参照してください。

# 参考文献

> Brendan J. Frey and Delbert Dueck. *データポイント間でメッセージを渡すことによるクラスタリング.* Science, vol 315, pages 972-976, 2007.

