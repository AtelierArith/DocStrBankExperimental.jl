```
BondTable(bondarray; description, collapsed)
```

入力として債券の配列を取り、入力配列内のすべての債券を表示する浮動テーブルを作成します。

`description`が提供されていない場合、デフォルトでテキスト*BondTable*になります。説明は文字列またはHTML出力のいずれかであることができます。

オプションの`collapsed`キーワード引数を使用して、BondTableを表示する際に折りたたまれた状態にするかどうかを指定できます。提供されない場合、BondTableは*折りたたまれません*。

BondTableの*折りたたまれた*状態は、BondTableを表示するセルの反応的な実行を通じて持続します。

参照: [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
