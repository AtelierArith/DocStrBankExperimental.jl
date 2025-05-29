```
in_phase_space_layout(out_psl::AbstractOutPhaseSpaceLayout)::AbstractInPhaseSpaceLayout
```

この関数は、[`AbstractOutPhaseSpaceLayout`](@ref) インターフェースのために実装する必要があります。出力の位相空間レイアウト（`out_psl`）を受け取り、この関数は関連する入力の位相空間レイアウトを返します。

これは、散乱過程における位相空間点を計算またはサンプリングする際に、入力および出力の粒子運動量間の一貫性を確保するために便利です。

## 引数

  * `out_psl`: 出力の位相空間レイアウトで、[`AbstractOutPhaseSpaceLayout`](@ref) のサブタイプです。

## 戻り値

  * 関連する入力の位相空間レイアウトで、[`AbstractInPhaseSpaceLayout`](@ref) のサブタイプです。
