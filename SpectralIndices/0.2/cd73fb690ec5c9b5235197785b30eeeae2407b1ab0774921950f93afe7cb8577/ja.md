```
Constant(constant::Dict{String, Any}) -> Constant
```

辞書から `Constant` オブジェクトを作成します。

# 引数

  * `constant::Dict{String, Any}`: 次のキーを含む辞書：

      * `"description"`: 定数の説明。
      * `"short_name"`: 定数の短い名前。
      * `"default"`: 定数のデフォルト値。

# 戻り値

  * `Constant`: 提供された辞書に基づいてフィールドが populated された `Constant` 構造体のインスタンス。

# 例

```julia
constant_dict = Dict(
    "description" => "Speed of light in vacuum", "short_name" => "c", "default" => 299792458
)
constant = Constant(constant_dict)
```
