```
IndexFunArray([T], gen::F, size::NTuple{N,Int}) where {N,F}
```

配列のように振る舞うが、完全な配列を割り当てない `IndexFunArray` オブジェクトを生成します。代わりに、必要に応じて要素を計算します。これは配列の割り当てを防ぐのに役立ちます。`gen` は、タプルとしてラップされた配列インデックスを入力として受け取る関数です。`gen` の出力は、結果の配列の要素型を決定します。`size` は結果の配列の出力サイズです。`T` は配列のオプションの要素型です。`gen` は戻り値の型として `T` を持つ必要があり、そうでないと `IndexFunArray` は型が不安定になる可能性があります。

# 例

```julia-repl
julia> IndexFunArray(x -> sum(x), (3, 3))
3×3 IndexFunArray{Int64, 2, var"#182#183"}:
 2  3  4
 3  4  5
 4  5  6

julia> IndexFunArray(x -> sum(abs2.(x)), (3, 3))
3×3 IndexFunArray{Int64, 2, var"#184#185"}:
  2   5  10
  5   8  13
 10  13  18

julia> IndexFunArray(x -> (x[1], x[2], "Julia"), (3,3))
3×3 IndexFunArray{Tuple{Int64, Int64, String}, 2, var"#18#19"}:
 (1, 1, "Julia")  (1, 2, "Julia")  (1, 3, "Julia")
 (2, 1, "Julia")  (2, 2, "Julia")  (2, 3, "Julia")
 (3, 1, "Julia")  (3, 2, "Julia")  (3, 3, "Julia")
```
