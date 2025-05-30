クリックするたびに同じ値を返すボタン。

これを使用して*リアクティブセル*を*トリガー*できます。

**詳細は[`CounterButton`](@ref)を参照**して、ボタンがクリックされた*回数*を取得します。

## 例

1つのセルで：

```julia
@bind go Button("Go!")
```

別のセルで：

```julia
begin
	# バウンド変数を参照 - ボタンをクリックするとこのセルが実行されます
	go

	md"My favorite number is $(rand())!"
end
```
