```
to_toml([f::Function], io::IO, option; sorted=false, by=identity, kw...)
```

インスタンス `option` をオプション型から TOML に変換し、`IO` に書き込みます。その他の有効なキーワードオプションについては [`to_dict`](@ref) を参照してください。また、`sorted`、`by`、および `f` の説明については標準ライブラリの `TOML.print` を参照してください。

# `nothing` を除外する

TOML 仕様では、[null 型は存在しません](https://github.com/toml-lang/toml/issues/802)。指定されていないフィールド（Julia では値が `nothing`）は除外する必要があります。`to_toml` ではオプション `exclude_nothing` は常に `true` です。

ほとんどの場合、`nothing` は別の型と共に使用されてオプションまたは指定されていないフィールドを示すため、オプション構造体には常にデフォルト値 `nothing` を設定する必要があります。例えば、

次のように定義する必要があります。

```julia
@option struct OptionX
    a::Union{Nothing, Int} = nothing
    b::Maybe{Int} = nothing
end
```

ここで `Maybe{T}` は `Union{Nothing, T}` の便利なエイリアスです。
