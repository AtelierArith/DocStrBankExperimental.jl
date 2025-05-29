```
PowerManifold{𝔽,TM<:AbstractManifold,TSize,TPR<:AbstractPowerRepresentation} <: AbstractPowerManifold{𝔽,TM}
```

パワーマニフォールド $\mathcal M^{n_1× n_2 × … × n_d}$ はパワー幾何学を持っています。 `TSize` は各軸に沿った要素の数を定義し、`TypeParameter` を使用して静的に定義するか、フィールドに格納します。

例えば、マニフォールド値の時系列は、$d$ が 1 で $n_1$ がサンプルの数に等しいパワーマニフォールドによって表されます。マニフォールド値の画像（例えば拡散テンソル画像）は、幅と高さが画像の $n_1$ と $n_2$ に等しい二軸のパワーマニフォールド ($d=2$) によって表されます。

マニフォールドのサイズは静的ですが、パワーマニフォールド上の点は静的サイズの配列では表されません。

# コンストラクタ

```
PowerManifold(M::PowerManifold, N_1, N_2, ..., N_d; parameter::Symbol=:field)
PowerManifold(M::AbstractManifold, NestedPowerRepresentation(), N_1, N_2, ..., N_d; parameter::Symbol=:field)
M^(N_1, N_2, ..., N_d)
```

パワーマニフォールド $M^{N_1 × N_2 × … × N_d}$ を生成します。デフォルトでは、[`PowerManifold`](@ref) はさらに拡張されます。すなわち、`M=PowerManifold(N, 3)` の場合、`PowerManifold(M, 2)` は `PowerManifold(N, 3, 2)` と同等です。点はその後、`N` 上の点の 3×2 行列になります。コンストラクタの第二引数に [`NestedPowerRepresentation`](@ref) を提供することで、マニフォールドをネストすることができます。すなわち、`PowerManifold(M, NestedPowerRepresentation(), 2)` は、要素が `N` 上の点の長さ 3 のベクトルである長さ 2 のベクトルをネストされた配列表現で表します。

第三のシグネチャ `M^(...)` は最初のものと同等であり、したがって、パワーマニフォールドの組み合わせを *1つの* 大きなパワーマニフォールドにするか、デフォルトの表現を持つパワーマニフォールドを生成します。

このインターフェース内にはデフォルトの [`AbstractPowerRepresentation`](@ref) がないため、`^` 演算子は `PowerManifold` のみで利用可能であり、次元を連結します。

`parameter`: 型パラメータを使用して `n` を格納するかどうか。デフォルトではサイズはフィールドに格納されます。値は `:field` または `:type` のいずれかです。
