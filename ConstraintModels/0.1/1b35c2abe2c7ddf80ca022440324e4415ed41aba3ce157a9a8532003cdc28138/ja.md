```
sudoku(n; start= Dictionary{Int, Int}(), modeler = :JuMP)
```

ドメイン `1:n²` の数独問題のモデルを作成します。`modeler` 引数は、ソルバー内部モデル、MathOptInterfaceモデル、JuMPモデルをそれぞれ指す :raw, :MOI, :JuMP（デフォルト）を受け入れます。

```julia
# 数独 9×9 のための JuMP モデル `m` とその関連行列 `grid` を構築します
m, grid = sudoku(3)

# 開始インスタンスを使用した同様の処理
instance = [
    9  3  0  0  0  0  0  4  0
    0  0  0  0  4  2  0  9  0
    8  0  0  1  9  6  7  0  0
    0  0  0  4  7  0  0  0  0
    0  2  0  0  0  0  0  6  0
    0  0  0  0  2  3  0  0  0
    0  0  8  5  3  1  0  0  2
    0  9  0  2  8  0  0  0  0
    0  7  0  0  0  0  0  5  3
]
m, grid = sudoku(3, start = instance)

# ソルバーを実行します
optimize!(m)

# 値を取得して表示します
solution = value.(grid)
display(solution, Val(:sudoku))
```
