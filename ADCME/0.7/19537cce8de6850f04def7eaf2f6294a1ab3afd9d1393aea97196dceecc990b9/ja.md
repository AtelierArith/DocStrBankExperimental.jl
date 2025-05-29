```
customop(;with_mpi::Bool = false)
```

新しいカスタムオペレーターを作成します。通常、ユーザーは `customop` を2回呼び出します：最初の呼び出しは `customop.txt` を生成し、ユーザーはそのファイルの内容を編集します。2回目の呼び出しは、`customop.txt` から C++ ソースコード、CMakeLists.txt、および gradtest.jl を生成します。

# 例

```julia-repl
julia> customop() # 編集可能な `customop.txt` ファイルを作成
[ Info: カスタムオペレーターのために custom_op.txt を編集してください
julia> customop() # `customop.txt` を編集した後、再度呼び出してインターフェースファイルを生成します。
```

# オプション

  * `with_mpi`: カスタムオペレーターが MPI を使用するかどうか
