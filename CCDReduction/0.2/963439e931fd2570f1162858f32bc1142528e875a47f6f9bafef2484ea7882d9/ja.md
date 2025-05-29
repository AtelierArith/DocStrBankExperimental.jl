```
filenames(f,
          collection;
          path = nothing,
          save_prefix = nothing,
          save_suffix = nothing,
          save = any(!isnothing, (save_prefix, path, save_suffix)),
          save_delim = "_",
          ext = r"fits(\.tar\.gz)?"i,
          kwargs...)
```

コレクションのファイルパスを反復処理し、各ステップで関数 `f` を適用します。

`f` からの出力は、適切なキーワード引数を使用して保存できます。`save_prefix` 引数は、各ファイル名に `save_delim` で区切られたプレフィックスを追加します。`save_suffix` は拡張子の前にサフィックスを追加し、これは `ext` を介して手動で提供できます。これは [`fitscollection`](@ref) に似ています。ファイルは、`path` が指定されない限り、保存されているディレクトリに保存されます。最後に、`save` は前の引数のいずれかが設定されている場合、デフォルトで `true` になりますが、手動でオーバーライドすることもできます（テストに便利です）。ファイルは [`CCDReduction.writefits`](@ref) を使用して保存されます。

# 例

```julia
collection = fitscollection("~/data/tekdata")
data = map(filenames(collection)) do path
    fh = FITS(path)
    data = getdata(fh[1]) # assuming all 1-hdu are ImageHDUs
    close(fh)
    data
end
```

上記は、`collection` に存在する FITS ファイルパスの 1st hdu に対応する画像配列からなる `data` を生成します。操作を行いながら `data` を同時に保存するためには

```julia
data = map(filenames(collection; path = "~/data/tekdata", save_prefix = "retrieved_from_filename")) do img
    fh = FITS(path)
    data = getdata(fh[1]) # assuming all 1-hdu are ImageHDUs
    close(fh)
    data
end
```

取得したデータは、ユーザーが指定した `path = "~/data/tekdata"` に `retrieved_from_filename_(original_name)` (FITS ファイル) として保存されます。
