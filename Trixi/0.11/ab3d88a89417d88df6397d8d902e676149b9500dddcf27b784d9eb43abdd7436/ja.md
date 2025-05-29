```
min_max_speed_davis(u_ll, u_rr, orientation::Integer, equations)
min_max_speed_davis(u_ll, u_rr, normal_direction::AbstractVector, equations)
```

左状態 `u_ll` と右状態 `u_rr` のリーマン問題の最小および最大波速の簡単で迅速な推定。通常、`u_ll` と `u_rr` に関連する局所波速のみに基づいています。

  * S.F. Davis (1988) 簡略化された二次ゴドノフ型法 [DOI: 10.1137/0909030](https://doi.org/10.1137/0909030)

次の文献の式 (10.38) を参照してください。

  * Eleuterio F. Toro (2009) リーマンソルバーと流体力学の数値法: 実用的な入門 [DOI: 10.1007/b79761](https://doi.org/10.1007/b79761)

また、[`FluxHLL`](@ref)、[`min_max_speed_naive`](@ref)、[`min_max_speed_einfeldt`](@ref) も参照してください。
