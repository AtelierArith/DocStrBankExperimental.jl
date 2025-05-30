```
popoutwrap(T)
```

`T`型の`StructBond`をラップする`Popout`を構築するための便利な関数です。これは、ネストされた`StructBond`型を作成したいときに便利です。

例えば、以下の2つの構造体があるとします。

```
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
end
Base.@kwdef struct LOL
	asd::ASD 
	text::String
end
```

次のコードを使用して、`ASD`を生成するウィジェットのポップアウトも含む`LOL`型のインスタンスを作成するための素敵なウィジェットを作成できます。

```
# ASDのウィジェットを定義
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

# LOLのウィジェットを定義
@fieldbond LOL begin
	asd = popoutwrap(ASD)
	text = TextField(;default = "いくつかのテキスト")
end
@fielddescription LOL begin
	asd = "このフィールドを生成するウィジェットを表示するにはアイコンをクリックしてください"
	text = "退屈な説明"
end
@bind lol StructBond(LOL)
```

ここで、`lol`は、指定されたウィジェットによって対話的に制御可能な各フィールドを持ち、各ウィジェットの隣にフィールド説明を表示する`LOL`型のインスタンスになります。

参照: [`BondTable`](@ref), [`StructBond`](@ref), [`Popout`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
