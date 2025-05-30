```
@typeasfield T = Widget
@typeasfield begin
	T1 = Widget1
	T2 = Widget2
	...
end
```

特定の型 `T`、`T1`、または `T2` に対してデフォルトのウィジェットを提供するマクロです。これは、[`@fieldbond`](@ref) を使用してカスタム型のためにより具体的なデフォルトを指定することで上書きできます。カスタム型が [`StructBond`](@ref) 内にラップされ、そのフィールドのカスタムウィジェットが定義されていない場合、show メソッドはこのマクロで定義されたフィールド型のものを使用します。

# 例

次の Julia コードは、フィールド `a` に対してデフォルトのウィジェットが定義されていないためエラーになります。

```
using PlutoExtras.StructBondModule
struct ASD 
	a::Int
end
StructBond(ASD)
```

[`@fieldbond`](@ref) を使用して `ASD` に特定の値を定義することに加えて、Int のデフォルトウィジェットを次のように定義することもできます。

```julia
@typeasfield Int = Slider(1:10)
```

これで `StructBond(ASD)` を呼び出すとエラーにならず、`ASD` のフィールド `a` のボンドとして `Slider(1:10)` がデフォルトで表示されます。
