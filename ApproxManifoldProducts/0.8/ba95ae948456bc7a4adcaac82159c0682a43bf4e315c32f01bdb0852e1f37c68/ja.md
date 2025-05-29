```julia
struct ManifoldKernelDensity{M<:ManifoldsBase.AbstractManifold, B<:(Union{var"#s20", var"#s19"} where {var"#s20"<:ApproxManifoldProducts.ManellicTree, var"#s19"<:KernelDensityEstimate.BallTreeDensity}), L, P<:AbstractArray}
```

オンマニフォールドカーネル密度信念。

ノート

  * 座標次元のリストによって特定された部分を許可します。例： `._partial = [1;3]`

      * 部分的な信念を構築する際には、指定された部分座標に必要な情報を持つ完全なポイントを使用してください。

開発ノート

  * WIP AMP 問題 41、マニフォールドプロダクト中に一般的な再収束を使用します。
