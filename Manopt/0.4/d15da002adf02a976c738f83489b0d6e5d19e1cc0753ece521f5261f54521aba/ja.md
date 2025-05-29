```
StopWhenTrustRegionIsExceeded <: StoppingCriterion
```

Steihaug-Toint切断共役勾配法において、次の反復のノルムが信頼領域の半径 $θ \leq \Vert Y_{k}^{*} \Vert_p$ より大きいかどうかをテストするファンクタであり、信頼領域を離れたときにアルゴリズムを終了します。

# フィールド

  * `reason`: 停止基準が達成された場合の停止理由を格納します。詳細は [`get_reason`](@ref) を参照してください。

# コンストラクタ

```
StopWhenTrustRegionIsExceeded()
```

次の反復のノルムが信頼領域の半径を超えた後に停止することを示すために、StopWhenTrustRegionIsExceededファンクタを初期化します。

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
