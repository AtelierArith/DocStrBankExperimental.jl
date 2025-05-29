```
 SimpleManifoldCachedObjective{O<:AbstractManifoldGradientObjective{E,TC,TG}, P, T,C} <: AbstractManifoldGradientObjective{E,TC,TG}
```

与えられた点 `p` に対して [`AbstractManifoldGradientObjective`](@ref) のシンプルなキャッシュを提供します。このキャッシュは、点 `p` と勾配 $\operatorname{grad} f(p)$ を `X` に、コスト値 $f(p)$ を `c` に格納します。

`X` と `c` は、その有効性を追跡するためのブール値を伴います。

# コンストラクタ

```
SimpleManifoldCachedObjective(M::AbstractManifold, obj::AbstractManifoldGradientObjective; kwargs...)
```

## キーワード

  * `p`:           （`rand(M)`）キャッシュを初期化するための多様体上の点
  * `X`:           （`get_gradient(M, obj, p)` または `zero_vector(M,p)`）勾配を格納するための接ベクトル、初期化については `initialize` も参照
  * `c`:           （`get_cost(M, obj, p)` または `0.0`）初期化時にコスト関数を格納するための値
  * `initialized`: （`true`）キャッシュされた `X` と `c` を初期化するかどうか。
