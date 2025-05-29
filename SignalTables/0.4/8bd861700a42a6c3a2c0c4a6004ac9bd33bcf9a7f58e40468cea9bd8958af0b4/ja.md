```
v_unit = unitAsParseableString(v::[Number|AbstractArray])::String
```

`v`の単位を`Unitful.uparse`で解析可能な文字列として返します。

これにより、たとえば、単位付きの量をJSONファイルに保存し、ファイルを読み込む際にそれを回復することができます。これは、`string(unit(v))`が`uparse`で解析できない文字列を返すため、現在のUnitful機能では（簡単には）実現できません。Juliaでは、`string(something)`が通常、再びJuliaによって解析可能な何かの文字列表現を返すため、これは異常な動作です。詳細については、[Unitful issue 412](https://github.com/PainterQubits/Unitful.jl/issues/412)を参照してください。

おそらく、`unitAsParseableString(..)`はすべての発生するケースを処理できないでしょう。

# 例

```julia
using SignalTables
using Unitful

s = 2.1u"m/s"
v = [1.0, 2.0, 3.0]u"m/s"

s_unit = unitAsParseableString(s)  # ::String
v_unit = unitAsParseableString(v)  # ::String

s_unit2 = uparse(s_unit)  # :: Unitful.FreeUnits{(m, s^-1), ..., nothing}
v_unit2 = uparse(v_unit)  # :: Unitful.FreeUnits{(m, s^-1), ..., nothing}

@show s_unit   # = "m*s^-1"
@show v_unit   # = "m*s^-1"

@show s_unit2  # = "m s^-1"
@show v_unit2  # = "m s^-1"
```
