```
ssf_perp(sys::System; apply_g=true, formfactors=nothing)
```

スピン構造因子の測定を $(I-𝐪⊗𝐪/q^2)$ による収束で指定します。収束した値は非偏光散乱強度の推定値を提供します。特異な限界 $𝐪 → 0$ では、収束行列はその回転平均 $(2/3) I$ に置き換えられます。

この関数は [`ssf_custom`](@ref) の特別なケースです。

# 例

```julia
# 原子1およびその対称的な同等物のために Co²⁺ フォームファクターを選択
formfactors = [1 => FormFactor("Co2")]
ssf_perp(sys; formfactors)
```
