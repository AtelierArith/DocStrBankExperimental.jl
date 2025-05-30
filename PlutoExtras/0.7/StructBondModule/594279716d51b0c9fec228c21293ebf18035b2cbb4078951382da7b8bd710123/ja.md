```
@fielddata typename block
```

カスタムウィジェットを `typename` の各フィールドに定義するための便利なマクロです。これは主に [`StructBond`](@ref) と組み合わせて使用することを意図しています。

例えば、次の構造体 `ASD` があるとします。次のコードを使用して、`ASD` 型のインスタンスを作成するための素敵なウィジェットを作成できます。

```
begin
Base.@kwdef struct ASD
	a::Int 
	b::Int
	c::String
	d::String
end
@fielddata ASD begin
	a = (md"マジカルフィールドのマークダウン説明", Slider(1:10))
	b = (@htl("<span>HTML説明のフィールド</span>"), Scrubbable(1:10))
	c = ("通常の文字列説明", TextField())
	d = TextField()
end
@bind asd StructBond(ASD)
end
```

ここで `asd` は、指定されたウィジェットによって各フィールドが対話的に制御可能な `ASD` 型のインスタンスになります。また、各ウィジェットの隣にフィールドの説明が表示されます。 `block` 内の各 `:(=)` の右側の引数は、単一の要素または2つの要素のタプルのいずれかであることができます。単一の要素が提供された場合、提供された値は `fieldbond` として解釈され、そのフィールドに表示するバンド/ウィジェットとなります。2つの要素が与えられた場合、最初の要素は説明に割り当てられ、2番目の要素は表示するバンドとなります。

関連情報: [`BondTable`](@ref), [`StructBond`](@ref), [`@NTBond`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fieldbond`](@ref), [`@fielddescription`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
