```
spoil(spin, spoiling, [nothing])
spoil(spinmc, spoiling, [workspace])
```

与えられたスピンに対して勾配または理想的なスポイリングをシミュレートします。`(A, B)`を返し、`A * M + B`が磁化`M`にスポイリングを適用します。`B`が`nothing`である場合（`IdealSpoiling`の場合）、`A * M`がスポイリングを適用し、`A`と`B`の両方が`nothing`である場合（`RFSpoiling`の場合）、スポイリングはありません。

`SpinMC`オブジェクトおよび`GradientSpoiling`と`RFandGradientSpoiling`の場合、`workspace isa BlochMcConnellWorkspace`です。Bloch-McConnell方程式を解くために近似行列指数を使用するには、代わりに`nothing`を渡してください。

## 注意

この関数は勾配または理想的なスポイリングのみをシミュレートし、*RFスポイリング*はシミュレートしません。RFスポイリングは、TRからTRまでのシーケンス内のRFパルスの位相を更新することによって実装する必要があります。

インプレースバージョンについては、[`spoil!`](@ref)を参照してください。 ```
