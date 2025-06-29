```
connectance(N::AbstractEcologicalNetwork)
```

リンクの数を可能な相互作用の数で割ったものです。単一部ネットワークでは、これは $L/S^2$ です。二部ネットワークでは、これは $L/(T × B)$ です。最大の接続性は常に1（すなわち、グラフが完全である）ですが、最小値（ネットワークが退化していないと仮定した場合）は *0* ではないことに注意する価値があります。代わりに、単一部ネットワークにおける最小相互作用数は `S-1` であり、二部ネットワークでは `max(T,B)` です。

したがって、接続性は次のアプローチを使用して0と1の間で変換できます：`m` を最小相互作用数、Co を測定された接続性とすると、修正された値は `(Co-m)/(1-m)` です。私たちの知る限り、これは標準的な慣行ではなく、したがってパッケージ内の関数としては推奨されていません。

#### 参考文献

  * Delmas, E., Besson, M., Brice, M.-H., Burkle, L.A., Dalla Riva, G.V., Fortin, M.-J., Gravel, D., Guimarães, P.R., Hembry, D.H., Newman, E.A., Olesen, J.M., Pires, M.M., Yeakel, J.D., Poisot, T., 2018. 生態ネットワークの種相互作用の分析。生物学的レビュー 112540. https://doi.org/10.1111/brv.12433
  * Dunne, J.A., 2006. 食物網のネットワーク構造, in: Dunne, J.A., Pascual, M. (Eds.), 生態ネットワーク：構造とダイナミクスのリンク。オックスフォード大学出版局, pp. 27–86.
  * Martinez, N.D., 1992. コミュニティ食物網における一定の接続性。アメリカ自然主義者 139, 1208–1218.
