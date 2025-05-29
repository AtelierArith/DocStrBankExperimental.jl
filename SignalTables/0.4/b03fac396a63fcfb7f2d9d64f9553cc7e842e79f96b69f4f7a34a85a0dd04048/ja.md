```
signal = Var(; kwargs...)::OrderedDict{Symbol,Any}
```

変数 *signal* 定義を辞書の形で返します。`kwargs...` は変数属性のキー/値ペアです。

*:values* キーは、独立信号（または k 番目の独立変数）を関数とする任意の要素型の *信号配列* を表します。*信号配列* は、独立信号 `[i1,i2,...,j1,j2,...]` において変数要素 `[j1,j2,...]` を保持するインデックスを持ちます。信号配列の要素が *定義されていない* 場合、その値は *missing* です。さらに、追加の属性を保存することができます。

以下のキーが認識されています（*:values* を除き、すべて *オプション* です。*:values* は直接定義されるか、:alias を介して定義されなければなりません）：

| key              | value (文脈から明らかでない場合は String 型)                                                                                                                                                           |
|:---------------- |:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `:values`        | Array{T,N}: `signal[:values][i1,i2,...j1,j2,...]` は、独立信号 `[i1,i2,...]` における値 `[j1,j2,...]` です。または、`signal[:values][i_k]` は k 番目の独立変数の値 `[i_k]` です。                                       |
| `:unit`          | String: すべての信号要素の単位（`Unitful.uparse` で解析可能）、例: `"kg*m*s^2"`。Array{String,N}: `signal[:unit][j1,j2,...]` は変数要素 `[j1,j2,...]` の単位です。                                                       |
| `:info`          | 信号の短い説明（= [FMI 3.0](https://fmi-standard.org/docs/3.0/) および [Modelica](https://specification.modelica.org/maint/3.5/MLS.html) の `description`）。                                          |
| `:independent`   | = true, 独立変数の場合（k 番目の独立変数は信号テーブルの k 番目の Var）                                                                                                                                             |
| `:variability`   | `"continuous", "clocked", "clock", "discrete",` または `"tunable"`（パラメータ）。                                                                                                                  |
| `:state`         | = true, 信号が (*continuous*, *clocked*, または *discrete*) 状態の場合。                                                                                                                             |
| `:der`           | String: [`getSignal`](@ref)`(signalTable, signal[:der])[:values]` は `signal[:values]` の *導関数* です。                                                                                        |
| `:clock`         | String: [`getSignal`](@ref)`(signalTable, signal[:clock])[:values]` は `signal[:values]` に関連付けられた *クロック* です（クロックティックでのみ定義され、それ以外は *missing* です）。`Vector{String` の場合、信号に関連付けられたクロックのセットです。 |
| `:alias`         | String: `signal[:values]` は [`getSignal`](@ref)`(signalTable, signal[:alias])[:values]` への *参照* です。*参照* は Var-signal が信号テーブルに追加されるときに設定され、属性がマージされます。                                    |
| `:interpolation` | 信号ポイントの補間（`"linear", "none"`）。提供されない場合、`interpolation` は `:variability` から推測され、それ以外の場合は補間は `"linear"` です。                                                                                |
| `:extrapolation` | 独立信号の値の外での外挿（`"none"`）。                                                                                                                                                                  |

さらに、任意の他の信号属性を希望するキーで `signal` に保存することができます。たとえば、[FMI 3.0](https://fmi-standard.org/docs/3.0/#definition-of-types) の *変数型* などです。

# 例

```julia
using SignalTables

t = (0.0:0.1:0.5)
t_sig = Var(values = t, unit=u"s",  independent=true)
w_sig = Var(values = sin.(t), unit="rad/s", info="モーターの角速度")
c_sig = Var(values = [1.0, missing, missing, 4.0, missing, missing],
            variability="clocked")
b_sig = Var(values = [false, true, true, false, false, true])
a_sig = Var(alias = "w_sig")
```
