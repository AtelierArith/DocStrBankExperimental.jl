```
(E::EllipticCurve)(coords::Vector; check::Bool = true)
```

座標 `coords` で指定された $E$ の点 $P$ を返します。`coords` はアフィン座標（`length(coords) == 2`）または射影座標（`length(coords) == 3`）のいずれかです。

デフォルトでは、点が $E$ 上にあるかどうかがチェックされます。これを無効にするには、`check = false` に設定します。

# 例

```jldoctest
julia> E = elliptic_curve(QQ, [1, 2]);

julia> E([1, -2])
(1 : -2 : 1)

julia> E([2, -4, 2])
(1 : -2 : 1)
```
