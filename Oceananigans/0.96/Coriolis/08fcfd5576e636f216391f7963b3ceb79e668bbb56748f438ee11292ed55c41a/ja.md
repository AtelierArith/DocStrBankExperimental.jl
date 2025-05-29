```
struct NonTraditionalBetaPlane{FT} <: AbstractRotation
```

緯度による回転ベクトルの局所的な垂直成分と局所的な水平成分の変動を考慮したコリオリの実装です。海洋モデルにおける「従来の」近似は、回転ベクトルの局所的な垂直成分のみを考慮します（[`BetaPlane`](@reface)を参照）。

この実装は、[Dellar2011](@citet)の第5節に基づいており、エネルギー、角運動量、およびポテンシャル渦度を保存します。

# 参考文献

Dellar, P. (2011). Variations on a beta-plane: Derivation of non-traditional     beta-plane equations from Hamilton's principle on a sphere. Journal of     Fluid Mechanics, 674, 174-195. doi:10.1017/S0022112010006464
