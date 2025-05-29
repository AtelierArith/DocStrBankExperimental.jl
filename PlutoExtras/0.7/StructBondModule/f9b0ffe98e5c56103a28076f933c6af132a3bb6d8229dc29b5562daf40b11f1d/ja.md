```
@BondsList 説明ブロック
```

`BondsList`を作成するための便利なマクロで、これはテーブルのようなHTML出力内にあるさまざまな債券（`@bind`で作成された）をグループ化したものです。これは[`BondTable`](@ref)内で使用できます。各債券はカスタム説明に関連付けることもできます。このマクロに対する2番目の入力として与えられる`block`は、各行が`description = bond`の形式の代入である`begin`または`let`ブロックでなければなりません。説明は、MIMEタイプ`text/html`の`show`メソッドを持つものであれば何でも構いません。

以下のコードに例の使用法が示されています：

```
@BondsList "私の債券グループ" let tv = PlutoUI.Experimental.transformed_value
	 # 変換された値を使用して、結びつけられた変数`freq`のGHzをHzに変換します
	"周波数 [GHz]" = @bind freq tv(x -> x * 1e9, Slider(1:10))
	md"高度 ``h`` [m]" = @bind alt Scrubbable(100:10:200)
end
```

これにより、周波数`freq`と高度`alt`の債券をグループ化したテーブルのような表示が作成されます。

[`StructBond`](@ref)とは異なり、`@BondsList`の出力は`@bind`を使用して結びつけることを意図していません。これは、既存の債券を単にグループ化するだけです。また、`StructBond`とは異なり、`BondsList`の各行は他の行とは独立して対応する債券を更新します。

`BondsList`を`StructBond`と識別し区別するのに役立ちます。

関連情報: [`BondTable`](@ref), [`@NTBond`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
