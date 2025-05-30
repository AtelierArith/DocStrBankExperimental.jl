```julia
MultiCheckBox(options::Vector; [default::Vector], [orientation ∈ [:row, :column]], [select_all::Bool])
```

チェックボックスのグループ - ユーザーは返す`options`を選択できます。`@bind`を介して返される値は、現在チェックされているアイテムのリストです。

参照: [`MultiSelect`](@ref)。

`options`は、ペアの配列`key::Any => value::String`でも構いません。`key`は`@bind`を介して返され、`value`が表示されます。

# キーワード引数

  * `defaults`は、初期状態でチェックされるべきオプションを指定します。
  * `orientation`は、オプションが`:row`または`:column`のどちらに配置されるべきかを指定します。
  * `select_all`は、「すべて選択」チェックボックスを含めるかどうかを指定します。

# 例

```julia
@bind snacks MultiCheckBox(["🥕", "🐟", "🍌"]))

if "🥕" ∈ snacks
    "Yum yum!"
end
```

```julia
@bind functions MultiCheckBox([sin, cos, tan])

[f(0.5) for f in functions]
```

```julia
@bind snacks MultiCheckBox(["🥕" => "🐰", "🐟" => "🐱", "🍌" => "🐵"]; default=["🥕", "🍌"])
```

```julia
@bind animals MultiCheckBox(["🐰", "🐱" , "🐵", "🐘", "🦝", "🐿️" , "🐝",  "🐪"]; orientation=:column, select_all=true)
```
