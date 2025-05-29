```
egrid = read_egrid(pth)
egrid, raw_egrid = read_egrid(pth, extra_out = true)
```

`pth` から EGRID ファイルを読み込みます。結果は Dict として提供され、Jutul メッシュを構築するために `mesh_from_grid_section` に渡すことができます。

# 注意事項

この関数は `resdata` Python パッケージがインストールされていることを必要とし、最初に PythonCall をインストールし、スクリプトまたは REPL に `using PythonCall` を記述すると、自動的に環境に追加されます。

主に `resdata.grid.Grid` を使用します。
