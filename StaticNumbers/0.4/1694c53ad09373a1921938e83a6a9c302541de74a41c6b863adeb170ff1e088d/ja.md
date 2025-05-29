`LengthRange(zeroth, step, length)`

LengthRangeは、その`zeroth`、`step`および/または`length`が`Static`数であることを許可する（しかし必須ではない）範囲です。

範囲の`zeroth`要素は最初の要素の前の要素です。範囲の一部ではありませんが、静的であることがしばしば便利です。たとえば、一般的な1:n範囲がスカラーで乗算される場合、zeroth要素は`StaticInteger{0}`のままであることができます。

`step`は範囲の連続する要素間の距離です。

`length`は`Integer`でなければなりません。`LengthRange`はその最後の要素ではなく、長さによってパラメータ化されます。これにより、範囲にオフセットが追加されても長さが`Static`のままであることが可能になります。

`LengthRange`は、`OrdinalRange`および`AbstractUnitRange`のサブタイプである`LengthStepRange`と`LengthUnitRange`の和集合です。
