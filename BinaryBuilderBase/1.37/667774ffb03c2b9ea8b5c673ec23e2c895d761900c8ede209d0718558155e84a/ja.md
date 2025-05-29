```
supported_platforms(;exclude::Union{Vector{<:Platform},Function}=Returns(false),
                    experimental::Bool=false)
```

サポートされているプラットフォームのリストを `Platform` の配列として返します。 これらは、公式にビルドをサポートしているプラットフォームです。 `get_shard_hash()` にマッピングが表示されているがここに表されていない場合、それはおそらくそのプラットフォームがまだ「ベータ版」と見なされているためです。 `experimental=true` の場合、実験的と見なされるプラットフォームを含めます。

プラットフォームは、除外するプラットフォームの配列を `exclude` に指定することでリストから除外できます。つまり、`supported_platforms(exclude=[Platform("i686", "windows"), Platform("x86_64", "windows")])` または除外に対して true を返す関数を指定することができます。つまり、

```
supported_platforms(exclude=Sys.islinux)
```
