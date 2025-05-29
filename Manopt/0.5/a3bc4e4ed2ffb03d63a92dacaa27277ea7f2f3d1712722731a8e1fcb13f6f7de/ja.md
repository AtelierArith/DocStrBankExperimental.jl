```
 SimpleManifoldCachedObjective{O<:AbstractManifoldGradientObjective{E,TC,TG}, P, T,C} <: AbstractManifoldGradientObjective{E,TC,TG}
```

与えられた点 `p` に対して [`AbstractManifoldGradientObjective`](@ref) のシンプルなキャッシュを提供します。このキャッシュは、点 `p` と勾配 $\operatorname{grad} f(p)$ を `X` に、コスト値 $f(p)$ を `c` に格納します。

`X` と `c` は、それぞれの有効性を追跡するためのブール値を伴います。

# コンストラクタ

```
SimpleManifoldCachedObjective(M::AbstractManifold, obj::AbstractManifoldGradientObjective; kwargs...)
```

## キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: キャッシュを初期化するためのマニフォールド上の点
  * `X=get_gradient(M, obj, p)` または `zero_vector(M,p)`: 勾配を格納するための接ベクトル、`initialize=` も参照
  * `c=[`get_cost`](@ref)`(M, obj, p)`または`0.0`: コスト関数を格納するための値`initialize`
  * `initialized=true`: キャッシュされた `X` と `c` を初期化するかどうか。
