b, projection = ldiv2!(F::CholeskySpecialShifted{T,MT}, b::AbstractVector{T}; x0=zero(T))

`Mx=b` を解く、ここで F は M の特定の行と列が単位行列に設定された場合のコレスキー因子分解です。

解 `x` は `Mx=b` への `x0` からの射影です。`x0` はベクトルまたは数値（`fill(x0,n)` として扱われる）であることができます。

解が存在しない場合、`b` を空間 `Mx=0` への射影を見つけます。

`Mx=b` の解が見つかった場合は `projection=false`、見つからなかった場合は `projection=true` です。

`b` を上書きして返します。
