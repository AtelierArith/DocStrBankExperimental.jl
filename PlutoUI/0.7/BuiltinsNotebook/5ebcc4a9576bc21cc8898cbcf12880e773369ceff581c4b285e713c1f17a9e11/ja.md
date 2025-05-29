```julia
MultiSelect(options::Vector; [default], [size::Int])
# またはカスタム表示値を使用する場合:
MultiSelect(options::Vector{Pair{Any,String}}; [default], [size::Int])
```

マルチセレクタ - ユーザーは `options` の中から1つ以上を選択できます。

1つの選択アイテムのみを許可するバージョンについては、[`Select`](@ref)を参照してください。

# 例

```julia
@bind vegetables MultiSelect(["potato", "carrot"])

if "carrot" ∈ vegetables
	"yum yum!"
end
```

```julia
@bind chosen_functions MultiSelect([sin, cos, tan, sqrt])

[f(0.5) for f in chosen_functions]
```

ペア `bound_value => display_value` を指定することで、表示値を設定することもできます:

```julia
@bind chosen_functions MultiSelect([
	cos => "cosine function", 
	sin => "sine function",
])

[f(0.5) for f in chosen_functions]
```

`size` キーワード引数を使用して、一度に表示される行数を指定することができます。

```julia
@bind letters MultiSelect(string.('a':'z'), size=20)
```
