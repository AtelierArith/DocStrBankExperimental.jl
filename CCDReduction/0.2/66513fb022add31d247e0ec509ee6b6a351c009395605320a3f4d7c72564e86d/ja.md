```
arrays(f,
       collection;
       path = nothing,
       save_prefix = nothing,
       save_suffix = nothing,
       save = any(!isnothing, (save_prefix, path, save_suffix)),
       save_delim = "_",
       ext = r"fits(\.tar\.gz)?"i,
       kwargs...)
```

コレクションの画像配列を反復処理し、各ステップで関数 `f` を適用します。

`f` からの出力は、適切なキーワード引数を使用して保存できます。`save_prefix` 引数は、`save_delim` で区切られた各ファイル名にプレフィックスを追加します。`save_suffix` は拡張子の前にサフィックスを追加し、これは `ext` を介して手動で提供できます。これは [`fitscollection`](@ref) に似ています。ファイルは、`path` が指定されていない限り、保存されているディレクトリに保存されます。最後に、`save` は以前の引数のいずれかが設定されている場合、デフォルトで `true` になりますが、手動でオーバーライドすることもできます（テストに便利です）。ファイルは [`CCDReduction.writefits`](@ref) を使用して保存されます。

# 例

```julia
collection = fitscollection("~/data/tekdata")
processed_images = map(arrays(collection)) do arr
    trim(arr, (:, 1040:1059))
end
```

上記は、`collection` に存在する画像配列のトリミングされたバージョンで構成される `processed_images` を生成します。操作を行いながら `processed_images` を同時に保存するためには

```julia
processed_images = map(arrays(collection; path = "~/data/tekdata", save_prefix = "trimmed")) do img
    trim(img, (:, 1040:1059))
end
```

トリミングされた画像配列は、ユーザーが指定した `path = "~/data/tekdata"` に `trimmed_(original_name)` (FITSファイル) として保存されます。
