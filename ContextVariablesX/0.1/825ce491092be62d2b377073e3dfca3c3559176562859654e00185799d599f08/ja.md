```
with_context(f, var1 => value1, var2 => value2, ...)
with_context(f, pairs)
```

指定された値がコンテキスト変数に設定された状態で `f` を実行します。この形式で指定された変数は、`with_context` が戻ると元の値にロールバックされます。これは動的スコープの `let` のように動作します。値として `nothing` が渡されると、対応するコンテキスト変数はクリアされます。つまり、未割り当てになるか、デフォルト値を取ります。`value` が `nothing` になり得る場合は、`Some(value)` を使用して `value` を設定します。

```
with_context(f, nothing)
```

新しい空のコンテキストで `f` を実行します。`with_context` が戻ると、すべての変数は元の値に巻き戻されます。

注意してください

```julia
var2[] = value2
with_context(var1 => value1) do
    @show var2[]  # value2 を表示
    var3[] = value3
end
@show var3[]  # value3 を表示
```

および

```julia
var2[] = value2
with_context(nothing) do
    var1[] = value1
    @show var2[]  # デフォルトを表示 (または例外をスロー)
    var3[] = value3
end
@show var3[]  # value3 は表示されない
```

は同等ではありません。
