```julia
activate_notebook_environment(f::Function, notebook_path::String)
```

ノートブックファイルに埋め込まれたパッケージ環境を一時的にアクティブにし、スクリプト内で使用します。関数 `f` の中では、Pkgコマンドを使用して環境を変更でき、関数が終了した後に行った変更は自動的にノートブックファイルに保存されます。スレッドセーフではありません。

このメソッドは、ノートブックファイルを更新するスクリプトに最適です。対話的な使用には、メソッド `activate_notebook_environment(notebook_path::String)` を推奨します。

# 例

```julia
Pluto.activate_notebook_environment("notebook.jl") do
    Pkg.add("Example")
end

# これでファイル "notebook.jl" が更新されました！
```

!!! warning
    この関数はプライベートメソッド `Pkg.activate(f::Function, path::String)` を使用しています。このAPIは将来のJuliaバージョンでは利用できない可能性があります。🤷

