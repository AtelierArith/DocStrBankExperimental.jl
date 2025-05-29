# 関数呼び出し

`printuln(r...; label="")`

# 説明

この関数は、オプションで指定された単位で実数または複素数の変数を印刷します。

# 変数

`r[1]` 印刷されるテキスト文字列で、変数名または説明を示します。オプションの変数 `label` が指定されていない場合、最大16文字まで許可されます。変数 `label` が指定されている場合、`r[1]` の最大長は12文字を超えてはいけません。

`r[2]` 印刷される変数で、変数は実数または複素数であり、Unitfulモジュールから割り当てられた単位が許可されます。変数のベクトルも許可されます。

`r[3]` 表示される `r[2]` のオプションのターゲット単位。

`label` 変数の出力を構成するオプションの4文字ラベル、例：`label = "(a)"`

# 例

```julia
julia> using Unitful, Unitful.DefaultSymbols, ElectricalEngineering
julia> U1 = 300V+j*400V
julia> printuln("U1", U1, kV)
              U1 = 0.3 kV + j 0.4 kV
                 = 0.5 kV ∠ 53.1301°
julia> printuln("real(U1)", real(U1), kV)
        real(U1) = 0.3 kV
julia> printuln("U1", U1, V, label="(a)")
(a)           U1 = 300 V + j 400 V
                 = 500 V ∠ 53.1301°
```
