```
ccds(f,
     collection;
     path = nothing,
     save_prefix = nothing,
     save_suffix = nothing,
     save = any(!isnothing, (save_prefix, path, save_suffix)),
     save_delim = "_",
     ext = r"fits(\.tar\.gz)?"i,
     kwargs...)
```

コレクションの `CCDData` を反復処理し、各ステップで関数 `f` を適用します。

`f` からの出力は、適切なキーワード引数を使用して保存できます。`save_prefix` 引数は、`save_delim` で区切られた各ファイル名にプレフィックスを追加します。`save_suffix` は、拡張子の前にサフィックスを追加します。これは、[`fitscollection`](@ref) のように手動で提供できます。ファイルは、`path` が指定されない限り、保存されているディレクトリに保存されます。最後に、`save` は、前の引数のいずれかが設定されている場合はデフォルトで `true` になりますが、手動でオーバーライドすることもできます（テストに便利です）。ファイルは [`CCDReduction.writefits`](@ref) を使用して保存されます。

# 例

```julia
collection = fitscollection("~/data/tekdata")
processed_images = map(ccds(collection)) do img
    trim(img, (:, 1040:1059))
end
```

上記は、`collection` に存在する画像のトリミングされたバージョンで構成される `processed_images` を生成します。

処理を行いながら `processed_images` を同時に保存するためには

```julia
processed_images = map(ccds(collection; path = "~/data/tekdata", save_prefix = "trimmed")) do img
    trim(img, (:, 1040:1059))
end
```

トリミングされた画像は、ユーザーが指定した `path = "~/data/tekdata"` に `trimmed_(original_name)`（FITSファイル）として保存されます。
