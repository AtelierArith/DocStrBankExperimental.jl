```julia
save(
    filename,
    td;
    include_preamble,
    latex_engine,
    buildflags,
    dpi,
    showing_ide
)

```

引数を `filename` に保存します（[`TikzDocument`](@ref) または自動的にラップされた他のタイプ、例えば [`TikzPicture`](@ref)、[`Axis`](@ref)、または [`Plot`](@ref)）。ファイル拡張子から形式を推測します。キーワードはオプションを指定し、一部は特定の出力形式に特有です。

`pgfsave` はエクスポートされるエイリアスです。
