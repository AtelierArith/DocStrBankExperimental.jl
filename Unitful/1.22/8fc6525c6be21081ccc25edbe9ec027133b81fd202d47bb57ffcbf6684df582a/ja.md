```
@unit(symb,abbr,name,equals,tf,autodocs=false)
```

単位を定義します。[`@refunit`](@ref)のように次元を指定するのではなく、`equals`は定義されている単位の1つに等しい[`Unitful.Quantity`](@ref)である必要があります。`tf == true`の場合、10の累乗接頭辞ごとに記号が作成されます。`autodocs == true`の場合、SI接頭辞付き単位の自動生成されたドキュメント文字列が追加されます。このオプションは、`tf == false`の場合には影響を与えません。

!!! compat "Unitful 1.10"
    `@unit`呼び出しの前にドキュメント文字列を追加して結果の単位を文書化するには、Unitful 1.10以降が必要です。`autodocs`引数もUnitful 1.10以降が必要です。


`symb`がバインドされている[`Unitful.FreeUnits`](@ref)オブジェクトを返します。

使用例: `@unit mi "mi" Mile (201168//125)*m false`

この例では、`kmi`（キロマイル）は*生成されません*。
