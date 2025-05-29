@assertのように、引数に関する追加情報も出力しようとします。各引数は一度だけ評価されるため、通常のassertと比較して余分なオーバーヘッドはありません。

現在、以下のタイプの式に対して追加情報が返されます：

  * 関数呼び出し：例 `a <= b`、`bool_f(a,k1=...; k2...)`
  * 型アサート：例 `Type1 <: Type2`
  * 比較式：例 `a == b <= c + d <= e`

`@smart_assert`をコンパイル時に無効にする方法については、[`SmartAsserts.set_enabled`](@ref)を参照してください。

## 例

```julia
julia> let a = 1.0, rtol=0.1
           @smart_assert isapprox(a, sin(a), atol=0.05; rtol)
       end
ERROR: AssertionError: Condition `isapprox(a, sin(a), atol = 0.05; rtol)` failed due to:
        `a` evaluates to 1.0
        `sin(a)` evaluates to 0.8414709848078965
        `0.05` evaluates to 0.05
        `rtol` evaluates to 0.1
Stacktrace:
 ...
```
