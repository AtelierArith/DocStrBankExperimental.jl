```
compare(
    new_sol::SciMLBase.AbstractTimeseriesSolution,
    reference::DataFrame,
    over::Vector{<:Union{Pair{<:Any, String}, Pair{<:Any, Pair{String, String}}}}
    cmp=DefaultComparison(); warn_observed=true)
```

`compare`の低レベルバージョンで、`new_sol`内の値（変数 => 名前または変数 => (入力*名前, 出力*名前) ペアとして指定）を`reference`内の列名にマッピングすることができます。タプル結果バージョンでは、比較メソッドに渡されるときの列名を指定できます。マッピングが明示的であるため、このバージョンは`to_name`を取らず、しかし`warn_observed`は引き続き取ります。詳細については、`compare`の暗黙的比較バージョンを参照してください。
