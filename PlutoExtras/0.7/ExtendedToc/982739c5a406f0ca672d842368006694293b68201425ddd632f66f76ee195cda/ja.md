```
show_output_when_hidden(x)
```

与えられた入力 `x` を、`HypertextLiteral.@htl` で作成されたカスタム HTML コード内にラップし、呼び出し元の Pluto セルに `always-show-output` 属性を追加します。

これにより、セルが [`ExtendedTableOfContents`](@ref) セル非表示機能を使用して隠されている場合でも、HTML 内でセルの出力が表示され続けることが保証されます。これは、出力を生成するセルをノートブック内で隠されたセルとしてレンダリングできるようにするために主に便利です。

提供された属性は、CSS を介してセルが出力要素を除いて隠されたセルとまったく同じように見えることを保証します。出力が浮動している場合（[`BondTable`](@ref) や [`ExtendedTableOfContents`](@ref) のように）、これによりセルは隠され、レンダリングされた出力は表示されます。

# 使用例

```julia
BondTable([bonds...]) |> show_output_when_hidden
```

上記のコードは、`BondTable` を定義するセルをノートブックの隠された部分内に配置しながら、浮動する BondTable をレンダリングできるようにします。この関数がなければ、`BondTable` を生成するセルはノートブックの非隠された部分内に配置する必要があります。

# 注意

この関数を `HTML` または `HypertextLiteral.Result` 型でない入力オブジェクトで呼び出すと、関数は最初に `@htl` と `PlutoRunner.embed_display` を使用してオブジェクトをラップします。`embed_display` 関数は Pluto 内でのみ利用可能です。  
