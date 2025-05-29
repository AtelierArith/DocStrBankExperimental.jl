```
ssf_custom(f, sys::System; apply_g=true, formfactors=nothing)
```

カスタム収縮関数 `f` を用いてスピン構造因子の測定を指定します。この関数は、グローバルな直交座標系における波ベクトル $𝐪$ と、構造因子強度成分 $\mathcal{S}^{αβ}(𝐪,ω)$ を持つ 3×3 行列を受け取ります。インデックス $(α, β)$ はグローバル座標系における双極子成分を示します。`f` の戻り値は任意の数または `isbits` 型であることができます。特定の `f` の選択により、[`ssf_perp`](@ref) や [`ssf_trace`](@ref) で定義されたような測定を得ることができます。

デフォルトでは、g因子またはテンソルが各サイトで適用され、構造因子成分は磁気モーメント演算子間の相関を示します。裸のスピン演算子間の相関を測定するには、`apply_g=false` に設定します。

オプションの `formfactors` は、対称的に異なる原子の完全なセットである `i1, i2, ...` に対して、ペア `[i1 => FormFactor(...), i2 => ...]` のリストで構成され、各 [`FormFactor`](@ref) は指定された原子に対する $𝐪$-空間の減衰を実装します。

[`SpinWaveTheory`](@ref) および [`SampledCorrelations`](@ref) のインスタンスでの使用を意図しています。

# 例

```julia
# すべての構造因子成分 Sᵅᵝ を 3×3 行列として測定
measure = ssf_custom((q, ssf) -> ssf, sys)

# 構造因子トレース Sᵅᵅ を測定
measure = ssf_custom((q, ssf) -> real(ssf[1, 1] + ssf[2, 2] + ssf[3, 3]), sys)
```

構造因子の慣習に関する Sunny のドキュメントも参照してください [Structure Factor Conventions](@ref).
