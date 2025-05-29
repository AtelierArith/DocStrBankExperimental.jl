```
q_space_grid(cryst::Crystal, axis1, range1, axis2, range2; offset=[0,0,0], orthogonalize=false)
q_space_grid(cryst::Crystal, axis1, range1, axis2, range2, axis3, range3; orthogonalize=false)
```

均一な間隔のq点の2Dまたは3Dグリッドを返します。体積の形状は、逆格子単位（RLU）での`(axis1, axis2, ...)`によって定義されます。`(range1, range2, ...)`の要素は、グリッド位置を定義するために使用される係数$c_i$を提供します、

```julia
    offset + c1 * axis1 + c2 * axis2 + ...
```

非ゼロの`offset`は2Dの場合にのみ許可されます。

最初の範囲パラメータ`range1`は、規則的に間隔を空けた係数のリストでなければなりません。例えば、`range1 = range(lo1, hi1, n)`のようにします。後続の範囲パラメータは、グリッド間隔情報なしで、境界のペアである場合があります。例えば、`range2 = (lo2, hi2)`を選択することで、グローバルなデカルト座標系でほぼ均一なサンプリング密度を提供するために適切なステップサイズが推測されます。

軸は非直交である可能性があります。グローバルなデカルト座標系で直方体の体積に拡張するには、`orthogonalize=true`を設定します。

1Dグリッドの場合は、代わりに[`q_space_path`](@ref)を使用してください。
