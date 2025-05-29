```
StopWhenTrustRegionIsExceeded <: StoppingCriterion
```

Steihaug-Toint切断共役勾配法において、次の反復のノルムが信頼領域半径 $θ ≤ \lVert Y^{(k)}^{*} \rVert_{p^{(k)}}$ より大きいかどうかをテストし、信頼領域を離れたときにアルゴリズムを終了するためのファンクタです。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示した反復を示す整数で、ソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `trr` 信頼領域半径
  * `YPY` 計算された $Y$ のノルム。

# コンストラクタ

```
StopWhenTrustRegionIsExceeded()
```

次の反復のノルムが信頼領域半径を超えたときに停止することを示すために、StopWhenTrustRegionIsExceededファンクタを初期化します。

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref)
