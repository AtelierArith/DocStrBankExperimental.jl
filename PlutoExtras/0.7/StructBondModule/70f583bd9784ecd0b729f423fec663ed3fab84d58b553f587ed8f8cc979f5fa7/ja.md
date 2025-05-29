```
@NTBond 説明ブロック
@NTBond 説明ブロック transform_function
```

便利なマクロで、第二引数 `block` で提供されたフィールド名を持つ NamedTuple をラップする [`StructBond`](@ref) を作成します。

NamedTuple を生成するための迅速な方法が必要な場合に便利です。以下のコードに例を示します：

```
@bind nt @NTBond "My Fancy NTuple" begin
	a = ("説明", Slider(1:10))
	b = (md"*太字* フィールド", Slider(1:10))
	c = Slider(1:10) # 説明なし、フィールドの名前がデフォルト
end
```

これにより `NamedTuple{(:a, :b, :c)}` が作成され、変数 `nt` に割り当てられます。

マクロを第三引数付きで呼び出すと、これは `PlutoUI.Experimental.transformed_value` を使用してボンド変換を作成するための関数として解釈されます。

つまり、以下の二つの式は同じ結果をもたらします：

```julia
@NTBond "WoW" begin
	a = ("説明", Slider(1:10))
end x -> x.a + 2
```

と

```julia
PlutoUI.Experimental.transformed_value(x -> x.a + 2, @NTBond "WoW" begin
	a = ("説明", Slider(1:10))
end)
```

関連項目: [`BondTable`](@ref), [`@NTBond`](@ref), [`@BondsList`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
