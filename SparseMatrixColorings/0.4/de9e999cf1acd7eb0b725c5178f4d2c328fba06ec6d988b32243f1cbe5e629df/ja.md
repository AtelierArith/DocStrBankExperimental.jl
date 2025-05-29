```
ColoringProblem{structure,partition}
```

彩色問題を解決するためのセレクタ型で、複数のディスパッチを可能にします。

これは、メイン関数 [`coloring`](@ref) に引数として渡されます。

# コンストラクタ

```
ColoringProblem{structure,partition}()
ColoringProblem(; structure=:nonsymmetric, partition=:column)
```

  * `structure::Symbol`: `:nonsymmetric` または `:symmetric`
  * `partition::Symbol`: `:column`、 `:row` または `:bidirectional`

!!! warning
    2番目のコンストラクタ（キーワード引数に基づく）は型不安定です。


# 自動微分へのリンク

行列の彩色は自動微分でよく使用され、以下は翻訳ガイドです：

|       行列 |     モード |     `structure` |      `partition` | 実装済み |
| --------:| -------:| ---------------:| ----------------:| ----:|
| Jacobian | forward | `:nonsymmetric` |        `:column` |  yes |
| Jacobian | reverse | `:nonsymmetric` |           `:row` |  yes |
| Jacobian |   mixed | `:nonsymmetric` | `:bidirectional` |  yes |
|  Hessian |       - |    `:symmetric` |        `:column` |  yes |
|  Hessian |       - |    `:symmetric` |           `:row` |   no |
