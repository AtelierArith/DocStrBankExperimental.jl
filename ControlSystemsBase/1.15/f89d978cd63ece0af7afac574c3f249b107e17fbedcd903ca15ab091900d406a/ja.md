```
delay(tau)
delay(tau, Ts)
delay(T::Type{<:Number}, tau)
delay(T::Type{<:Number}, tau, Ts)
```

長さ `τ` の純粋な時間遅延をタイプ `T` で作成します。

タイプ `T` は `promote_type(Float64, typeof(tau))` にデフォルト設定されています。

`Ts` が指定されている場合、遅延はサンプリング時間 `Ts` で離散化され、離散時間の StateSpace オブジェクトが返されます。

# 例:

入力遅延 `L` を持つ LTI システムを作成します。

```julia
L = 1
tf(1, [1, 1])*delay(L)
s = tf("s")
tf(1, [1, 1])*exp(-s*L) # 上記のバージョンと同等
```
