```
create_string_converter(add_show_method::Bool = true)
```

HDF5.jlライブラリ（バージョン0.17.2）は、構造体内の`InlineStrings`や`StaticStrings`をサポートしていません。標準の`String`もエージェントおよびエッジタイプには適しておらず、これらはビットタイプである必要があります。

この制限に対処するために、`create_string_converter`は`String`と`SVector{N, UInt8}`インスタンス（`StaticArrays`パッケージから）との間の変換メソッドを生成します。ここで、Nは格納できる最大バイト数を表し、Unicode文字列の場合、可変長エンコーディングのために文字数を超えることがあります。

`SVector{N, UInt8}`の代わりに`VString{N}`も使用できます。

例えば、固定サイズの名前フィールドを持つPerson構造体を作成することができます：

```julia
struct Foo
    foo::VString{20}
end
```

その後、通常の文字列を使用して`Foo`インスタンスを構築できます：`Foo("abc")`。

`add_show_method`が`true`（デフォルト）に設定されている場合、これらの`SVector`に対しても`show`メソッドが定義されます。JuliaのREPLで作業しているときに、値が`String`として表示される一方で実際には`SVector`であるため混乱を避けるために、出力には値自体の後に"(as UInt8-Vector)"が含まれます。

`add_show_method`が`true`（デフォルトの動作）に設定されている場合、`SVector`タイプに対して`show`メソッドが自動的に定義されます。`SVector`の値が`String`として表示されることによる混乱を防ぐために、出力は値自体の後に注釈"::UInt8[]"を含むようにフォーマットされます。
