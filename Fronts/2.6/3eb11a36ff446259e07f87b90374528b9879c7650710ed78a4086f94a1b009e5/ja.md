```
diffusivity(prob::InverseProblem) -> Function
```

半無限一次元非線形拡散問題の解から拡散率関数 `D` を抽出します。この解は離散点のセットとして与えられます。

与えられた解をPCHIP単調スプラインで補間し、ブルースとクルートの方法を使用して `D` を再構築します。

補間に使用される方法のため、`D` は連続ですが、不連続な導関数を持ちます。

# 引数

  * `prob::InverseProblem`: 逆問題。 [`InverseProblem`](@ref) を参照してください。

# 参考文献

GERLERO, G. S.; BERLI, C. L. A.; KLER, P. A. 水平毛細管流の直接および逆解法のためのオープンソース高性能ソフトウェアパッケージ。 Capillarity, 2023, vol. 6, no. 2, p. 31-40.

BRUCE, R. R.; KLUTE, A. 土壌水分拡散率の測定。 Soil Science Society of America Journal, 1956, vol. 20, no. 4, p. 458-462.
