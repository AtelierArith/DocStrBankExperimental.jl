```julia
Select(options::Vector; [default])
# またはカスタム表示値を使用する場合:
Select(options::Vector{Pair{Any,String}}; [default::Any])
```

ドロップダウンメニュー - ユーザーは `options` ベクターの要素を選択できます。

複数の選択項目を許可するバージョンについては、[`MultiSelect`](@ref)を参照してください。

# 例

```julia
@bind veg Select(["potato", "carrot"])
```

```julia
@bind f Select([sin, cos, tan, sqrt])

f(0.5)
```

ペア `bound_value => display_value` を指定することで、表示値を指定することもできます:

```julia
@bind f Select([cos => "cosine function", sin => "sine function"])

f(0.5)
```
