```
StructBond(T;description = typedescription(T))
```

`@bind`を使用するためのHTMLウィジェットを作成し、各フィールドにウィジェットを割り当てることでカスタムタイプ`T`を定義できるようにします。ウィジェットは、各フィールドのdocstringが存在する場合はその説明を自動的に使用し、そうでない場合はフィールド名を使用します。

`@bind`と一緒に使用すると、さまざまなフィールドをキーワード引数として使用して`T`のインスタンスを自動的に生成します。*これは、構造体`T`が`Base.@kwdef`や`Parameters.@with_kw`で生成されるようなキーワード専用の構築をサポートしている必要があることを意味します。

機能するためには、ウィジェット（およびオプションで説明）を、タイプ`T`の各フィールドに関連付けるために便利なマクロ`@fielddata`を使用して提供する必要があります。

オプションの`description`キーワード引数はデフォルトでタイプ名に設定されていますが、`MIME"text/html"`として表示可能なものであれば何でも上書きできます。

関連情報: [`BondTable`](@ref), [`@NTBond`](@ref), [`@BondsList`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
