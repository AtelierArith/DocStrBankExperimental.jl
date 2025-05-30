```
@fieldbond typename block
```

`typename`の各フィールドにカスタムウィジェットを定義するための便利なマクロです。これは主に[`StructBond`](@ref)と組み合わせて使用することを意図しています。

例えば、次の構造体があるとします。

```
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
end
```

次のコードを使用して、`ASD`型のインスタンスを作成するための素敵なウィジェットを作成できます。

```
@fieldbond ASD begin
	a = Slider(1:10)
	b = Scrubbable(1:10)
	c = TextField()
end
@fielddescription ASD begin
	a = md"マジカルフィールドのマークダウン説明"
	b = @htl "<span>HTML説明のフィールド</span>"
	c = "通常の文字列説明"
end
@bind asd StructBond(ASD)
```

ここで、`asd`は`ASD`型のインスタンスであり、各フィールドは指定されたウィジェットによってインタラクティブに制御可能で、各ウィジェットの隣にフィールドの説明が表示されます。

関連情報: [`BondTable`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
