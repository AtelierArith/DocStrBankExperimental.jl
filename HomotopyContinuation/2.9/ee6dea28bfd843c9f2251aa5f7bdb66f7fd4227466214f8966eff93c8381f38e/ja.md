```
IntrinsicSubspaceHomotopy(F::System, V::LinearSubspace, W::LinearSubspace)
IntrinsicSubspaceHomotopy(F::AbstractSystem, V::LinearSubspace, W::LinearSubspace)
```

ホモトピー $H(x,t) = F(γ(t)x)$ を作成します。ここで、$γ(t)$ はアフィン部分空間のファミリーであり、$γ(1) = V$ および $γ(0) = W$ です。ここで、$γ(t)$ はアフィングラスマン多様体における `V` と `W` の間の測地線であり、すなわち `V` と `W` を接続する最小長の曲線です。さらに [`LinearSubspace`](@ref) および [`geodesic`](@ref) とそこにある参考文献も参照してください。
