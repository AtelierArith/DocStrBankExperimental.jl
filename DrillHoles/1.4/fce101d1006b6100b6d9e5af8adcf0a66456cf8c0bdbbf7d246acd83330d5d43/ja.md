```
Interval(table; [holeid], [from], [to])
```

インターバル `table` は、指定された `holeid` を持つ掘削孔に沿って、与えられた深さ `from` から別のより大きな深さ `to` までのインターバルを格納します（通常はメートル単位）。インターバルに加えて、`table` には、グレード、鉱化ドメイン、地質解釈などの変数の測定値が格納されます。

キーワード引数が省略された場合、一般的な列名が `table` で検索されます。

## 例

```julia
Interval(table, holeid="BHID", from="START", to="FINISH")
Interval(table, from="BEGIN", to="END")
```

参照：[ `Collar`](@ref), [ `Survey`](@ref).
