`showpic(p;opt...)` は、`Poset` または `CPoset` のハッセ図のグラフィカルな表現を `dot` および `open` コマンドを使用して表示します。`p isa Poset` の場合、キーワード引数として `IO` プロパティのリストを指定することができ、これらは `p` の `show_element` メソッドに転送されます。
