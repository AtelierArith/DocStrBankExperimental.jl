```
to_dict(::Type{T}, x, option::ToDictOption) where T
```

`x`を`T`のオプション型内にある場合に変換します。`option`は変換の動作を決定するためのオプションのセットです。これは`to_dict(x; kw...)`の動作を変更するためにオーバーロードできます。

```
to_dict(::Type{T}, x) where T
```

`x`がオプション型でない場合や含まない場合は、便利さのために2引数バージョンを使用することもできます。

# 例

以下はオプションのリストを処理するためのビルトインオーバーロードです。

```julia
function Configurations.to_dict(::Type{T}, x::Vector, option::ToDictOption) where T
    if is_option(eltype(x))
        return map(p->to_dict(T, p, include_defaults), x)
    else
        return x
    end
end
```

以下は、すべての種類のオプション型に対してすべての`VersionNumber`を`String`に変換するために2引数の`to_dict`をオーバーロードします。

```julia
Configurations.to_dict(::Type, x::VersionNumber) = string(x)
```
