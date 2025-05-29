```
PLists
```

これはXMLファイルを読み取る方法の簡単な例です。

```julia-repl
julia> doc = readxml("examples/note.xml");
julia> r = root(doc);
julia> ns = nodes(r);
```

子ノードや属性ノードを操作するために、配列または辞書インターフェースを使用できます。

NeXTまたはAppleスタイルのプロパティリストを読み取るには：

```julia-repl
julia> dict = readplist("test/example.plist")
```

これにより、操作できる通常の辞書が得られます。
