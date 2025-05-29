```
readprops(filename::AbstractString; subst_pathvar::Bool = true, subst_env::Bool = true, trim_null::Bool = true)
readprops(filenames::Vector{<:AbstractString}; ...)
```

単一または複数のJSONファイルから[`PropDict`](@ref)を読み込みます。

複数のファイルが指定された場合、それらは`merge`を使用して単一の`PropDict`にマージされます。

`subst_pathvar`は、`$_`が文字列値内のJSONファイルのディレクトリパスで置き換えられるべきかどうかを制御します（フィールド名ではなく）。

`subst_env`は、`$ENVVAR`が文字列値内の各環境変数`ENVVAR`の値で置き換えられるべきかどうかを制御します（フィールド名ではなく）。

`trim_null`は、JSONの`null`値が完全に削除されるべきかどうかを制御します。
