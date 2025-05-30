クリックされた回数を返すボタン。

これを使って*リアクティブセル*をトリガーできます。

## 例

1つのセルで：

```julia
@bind go CounterButton("Go!")
```

別のセルで：

```julia
begin
	# バウンド変数を参照 - ボタンをクリックするとこのセルが実行されます
	go

	md"My favorite number is 0.37067542116988217!"
end
```
