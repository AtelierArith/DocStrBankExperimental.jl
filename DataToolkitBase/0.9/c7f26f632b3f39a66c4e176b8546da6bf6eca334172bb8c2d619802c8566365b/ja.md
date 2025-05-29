```
create(T::Type{<:AbstractDataTransformer}, source::String, dataset::DataSet)
```

もし `source`/`dataset` が型 `T` のデータトランスフォーマーを構築するために使用できる場合は、それを構築して返します。そうでない場合は `nothing` を返します。

特定のトランスフォーマーは、この関数の特化した形式を実装する必要があり、適用できないことを示すために `nothing` を返すか、"create spec form" を返します。"create spec form" は、作成されるトランスフォーマーのプロパティを示す `key::String => value` エントリのリストです。例えば、

```
["foo" => "bar",
 "baz" => 2]
```

TOML表現可能な値を受け入れることに加えて、ユーザーに提示するインタラクティブなプロンプトを指定する `NamedTuple` 値を与えることもできます。

```
(; prompt::String = "$key",
   type::Type{String or Bool or <:Number} = String,
   default::type = false or "",
   optional::Bool = false,
   skipvalue::Any = nothing,
   post::Function = identity)
```

値は、現在の仕様を引数として受け取り、TOML表現可能な値または `NamedTuple` を返す `Function` であることもできます。

最後に、空の（パラメータなしの）ドライバーを作成するかどうかを単純に示す便利な方法として `true`/`false` を返すことができます。
