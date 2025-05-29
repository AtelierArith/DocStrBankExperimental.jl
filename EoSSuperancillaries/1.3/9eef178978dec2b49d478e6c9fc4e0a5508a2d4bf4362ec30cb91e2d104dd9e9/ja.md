```
ω = pcsaft_acentric(m)
```

PCSAFT状態方程式の非中心因子を返します。

入力:

  * `m`: セグメント長（単位なし）

出力:

  * `ω` : 非中心因子（単位なし）。付随的な範囲外の場合は`NaN`を返します（1 ≤ m ≤ 64）。

## 例

```julia-repl
julia> m = 1.0
(1.0, 150.03)

julia> Tc = pcsaft_acentric(m)
191.40058128833536
```
