```
dict_to_index(dict)
dict_to_index(symbol_val, dict)
```

辞書表現のインデックス `dict` をインデックスに変換します。

ユーザーは、[`index_to_dict`](@ref) とともにこのメソッドを拡張することによって、`dict_to_index`（およびそれに伴う `VarName` のデシリアライズ）機能を拡張できます。具体的には、カスタムインデックスタイプ `MyIndexType` を持ち、このインデックスタイプを含む `VarName` をデシリアライズ/シリアライズできるようにしたいとします。その場合、次の2つのメソッドを実装する必要があります。

1. `AbstractPPL.index_to_dict(i::MyModule.MyIndexType)` は、インデックス `i` の辞書表現を返す必要があります。この辞書にはキー `"type"` が含まれ、その対応する値はインデックスタイプを一意に識別する文字列でなければなりません。一般的に、この値には型の名前（モジュール修飾子を前に付けることもある）を使用して衝突を避けるのが理にかなっています。辞書の残りの部分は、任意の構造を持つことができます。
2. `index_to_dict(i)["type"]` の値が `"MyModule.MyIndexType"` であるとします。その場合、対応するメソッド `AbstractPPL.dict_to_index(::Val{Symbol("MyModule.MyIndexType")}, dict)` を実装する必要があります。このメソッドは、辞書表現を第二引数として受け取り、元の `MyIndexType` オブジェクトを返す必要があります。

これがどのように機能するかの例を見たい場合は、OffsetArrays のシリアライズに関するテストを含む AbstractPPL テストスイートを参照してください。
