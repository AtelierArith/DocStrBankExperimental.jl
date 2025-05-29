```
BiweightTransform(X; c=9, M=nothing)
```

バイウェイト変換に基づくイテレータを作成します。[^1] このイテレータは、最初にすべての入力データをフィルタリングし、有限の値のみが残るようにします。次に、イテレーションはカスタム状態を使用して進行し、値がカットオフ内にあるかどうかを示すフラグを含みます。カットオフは、中央値絶対偏差（MAD）の `c` 倍です。MADは `M` からの偏差に基づいており、`M` が `nothing` の場合は `X` の中央値がデフォルトになります。

!!! note "高度な使用法"
    この変換イテレータは `BiweightStats.jl` の内部計算に使用されるため、やや複雑なイテレータ実装を持っています。


# 例

```jldoctest transform
julia> X = randn(rng, 100);


julia> X[10] = 1e4 # 明確な外れ値を追加
10000.0

julia> X[13] = NaN # NaNを追加
NaN

julia> X[25] = Inf # Infを追加
Inf

julia> bt = BiweightTransform(X);

```

すべてのエントリが有限であることを確認しましょう。イテレーションインターフェースは次のように分かれています。

```julia
(d, u2, flag), state = iterate(bt, [state])
```

ここで `d` はデータ値から `M` を引いたもので、`u2` は `(d / (c * MAD))^2`、`flag` は値が変換されたデータセット内にあるかどうかです。

```jldoctest transform
julia> all(d -> isfinite(d[1]), bt)
true
```

そして、通常のサンプルと、インデックス `10` に手動で挿入した外れ値サンプルとの間でイテレーションがどのように異なるかを見てみましょう。

```jldoctest transform
julia> (d, u2, flag), _ = iterate(bt, 9)
((-0.17093842061187192, 0.0009098761083851183, true), 10)

julia> (d, u2, flag), _ = iterate(bt, 10)
((0.0, 0.0, false), 11)
```

# 参考文献

[^1]: [NIST: biweight](https://www.itl.nist.gov/div898/software/dataplot/refman2/ch2/biweight.pdf)
