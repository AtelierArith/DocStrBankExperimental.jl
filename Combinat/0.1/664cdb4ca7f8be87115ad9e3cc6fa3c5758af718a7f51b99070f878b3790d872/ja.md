`collectby(f,v)`

`v`の要素を、`f`が同じ値を取るパケット（`Vector`）にグループ化します。結果の`Vector{Vector}`は、`f`の値でソートされます（`f`の値はソート可能でなければなりません。そうでない場合は、遅い`values(groupby(f,v))`を使用できます）。ここで、`f`は1変数の関数または`v`と同じ長さのコレクションであることができます。

```julia-repl
julia> l=[:Jan,:Feb,:Mar,:Apr,:May,:Jun,:Jul,:Aug,:Sep,:Oct,:Nov,:Dec];

julia> collectby(x->first(string(x)),l)
8-element Vector{Vector{Symbol}}:
 [:Apr, :Aug]
 [:Dec]
 [:Feb]
 [:Jan, :Jun, :Jul]
 [:Mar, :May]
 [:Nov]
 [:Oct]
 [:Sep]

julia> collectby("JFMAMJJASOND",l)
8-element Vector{Vector{Symbol}}:
 [:Apr, :Aug]
 [:Dec]
 [:Feb]
 [:Jan, :Jun, :Jul]
 [:Mar, :May]
 [:Nov]
 [:Oct]
 [:Sep]
```
