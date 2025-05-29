```
reparametrize_global(ode, options...)
```

`ode`の再パラメータ化を、グローバルに同定可能な関数に関して見つけます。

タプル（`new_ode`、`new_vars`、`implicit_relations`）を返します。ここで：

  * `new_ode`は再パラメータ化されたODEシステムです。
  * `new_vars`は新しい変数から元の変数へのマッピングです。
  * `relations`は`new_vars`間の暗黙的代数関係の配列です。通常、`relations`は空です。

## オプション

この関数は以下のオプション引数を受け付けます。

  * `seed`: 0から1の範囲の浮動小数点数、ランダムシード（デフォルトは`seed = 42`）。
  * `prob_threshold`: 正確性の確率（デフォルトは`prob_threshold = 0.99`）。

## 例

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x1'(t) = a * x1(t) - b*x1(t)*x2(t),
    x2'(t) = -c * x2(t) + d*x1(t)*x2(t),
    y(t) = x1(t)
)

new_ode, new_vars, relations = reparametrize_global(ode)
```

次のようになります：

```
# new_ode
X2'(t) = X1(t)*X2(t)*a2 - X2(t)*a1
X1'(t) = -X1(t)*X2(t) + X1(t)*a3
y1(t) = X1(t)

# new_vars
Dict{Nemo.QQMPolyRingElem, AbstractAlgebra.Generic.FracFieldElem{Nemo.QQMPolyRingElem}} with 6 entries:
  X2 => b*x2
  y1 => y
  X1 => x1
  a2 => d
  a3 => a
  a1 => c
```

`new_ode`は完全に同定可能であり、元のものと比較して`1`つ少ないパラメータを持つことに注意してください。
