```
find_identifiable_functions(ode::ODE; options...)
```

与えられたODEシステムで識別可能なパラメータ/状態のすべての関数を見つけます。

## オプション

この関数は次のオプション引数を取ります：

  * `with_states`: `true`の場合、ODE状態における識別可能な関数も報告します。デフォルトは`false`です。
  * `simplify`: 出力関数がどの程度簡略化されるか。強い簡略化はより多くの時間を要する場合があります。可能なオプションは：

      * `:standard`: デフォルトの簡略化。
      * `:weak`: 弱い簡略化。このオプションは最も速いですが、出力関数はかなり複雑になる可能性があります。
      * `:strong`: 強い簡略化。このオプションは最も遅いですが、出力関数はきれいでシンプルです。
      * `:absent`: 簡略化なし。
  * `known_ic`: 初期条件が既知であると仮定される関数のリスト。これにより、返される識別可能な関数は状態ではなくパラメータと初期条件の関数になります（これは実験的な機能です）。
  * `prob_threshold`: 0から1の範囲の浮動小数点数、正確性の確率。デフォルトは`0.99`です。
  * `seed`: rngシード。デフォルト値は`42`です。
  * `loglevel` - 表示するログメッセージの最小レベル（デフォルトは`Logging.Info`）

## 例

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x0'(t) = -(a01 + a21) * x0(t) + a12 * x1(t),
    x1'(t) = a21 * x0(t) - a12 * x1(t),
    y(t) = x0(t)
)

find_identifiable_functions(ode)

# prints
3-element Vector{AbstractAlgebra.Generic.FracFieldElem{Nemo.QQMPolyRingElem}}:
 a12 + a01 + a21
 a12*a01
```
