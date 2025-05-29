```julia
confirm(element::Any; label::Union{String, Nothing}=nothing)
```

通常、[`Slider`](@ref)を動かしたり、[`TextField`](@ref)に入力したりすると、すべての中間値が`@bind`に送信されます。

入力要素を`confirm`でラップすることで、値が送信されるタイミングを手動で制御するボタンが得られ、中間更新はPlutoから隠されます。

これが便利なケースの一つは、`@bind`入力に基づいて長い計算を行うノートブックです。

`label`は確認ボタンのカスタムラベルを指定します。

# 例

```julia
@bind x confirm(Slider(1:100))

x == 1 # (初期状態)
```

スライダーを動かしても何も起こらず、`"Confirm"`ボタンをクリックするまで、`x`は新しいスライダー値に設定されません。

> 結果は次のようになります：
>
> ![screenshot of running the code above in pluto](https://user-images.githubusercontent.com/6933510/145615211-2731f1f5-5c7d-4aac-9aa5-8afe89e24a6b.png)


# 参照

これを[`PlutoUI.combine`](@ref)と組み合わせることができます！

```julia
@bind speeds confirm(
	combine() do Child
		@htl("""
		<h3>風速</h3>
		<ul>
		$([
			@htl("<li>$(name): $(Child(name, Slider(1:100)))")
			for name in ["北", "東", "南", "西"]
		])
		</ul>
		""")
	end
)
```

> 結果は次のようになります：
>
> ![screenshot of running the code above in pluto](https://user-images.githubusercontent.com/6933510/145614965-7a1e8630-4766-4589-8a84-b022bdfb09fc.gif)

