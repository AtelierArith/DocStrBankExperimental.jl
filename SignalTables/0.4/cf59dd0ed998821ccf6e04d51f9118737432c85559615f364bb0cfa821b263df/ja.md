```
signal = Par(; kwargs...)::OrderedDict{Symbol,Any}
```

パラメータ信号定義を辞書の形で返します。パラメータは、定数であり、独立変数の関数ではない変数です。`kwargs...`はパラメータ属性のキー/値ペアです。

パラメータ変数の値は、`signal`のキー*:value*に格納され、任意のJulia型（数値、文字列、配列、タプル、辞書など）のインスタンスです。

以下のキーが認識されます（すべて*オプション*です）：

| key      | value (文脈から明らかでない場合はString型)                                                                                                           |
|:-------- |:-------------------------------------------------------------------------------------------------------------------------------------- |
| `:value` | `signal[:value]`は、すべての独立信号の値に対して保持される定数値です。                                                                                            |
| `:unit`  | 文字列: すべての信号要素の単位（`Unitful.uparse`で解析可能）、例: `"kg*m*s^2"`。Array{String,N}: `signal[:unit][j1,j2,...]`は変数要素`[j1,j2,...]`の単位です。            |
| `:info`  | 信号の短い説明（= [FMI 3.0](https://fmi-standard.org/docs/3.0/)および[FMI](https://specification.modelica.org/maint/3.5/MLS.html)の`description`）。 |
| `:alias` | 文字列: `signal[:value]`は[`getSignal`](@ref)`(signalTable, signal[:alias])[:value]`への*参照*です。*参照*は設定され、Par信号が信号テーブルに追加されると属性がマージされます。      |

さらに、任意の他の信号属性を、*FMI 3.0*の*Variable Types*のように、希望するキーで`signal`に格納できます。

# 例

```julia
using SignalTables

J         = Par(value = 0.02, unit=u"kg*m/s^2", info="モーター慣性")
fileNames = Par(value = ["data1.json", "data2.json"])
J_alias   = Par(alias = "J")
```
