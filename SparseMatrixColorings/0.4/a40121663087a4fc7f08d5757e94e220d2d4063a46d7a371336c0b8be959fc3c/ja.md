```
AbstractColoringResult{structure,partition,decompression}
```

色付けアルゴリズムの結果のための抽象型です。

これは、主関数 [`coloring`](@ref) によって返されるオブジェクトのスーパタイプです。

# 型パラメータ

[`ColoringProblem`](@ref) と [`GreedyColoringAlgorithm`](@ref) の型パラメータの組み合わせ：

  * `structure::Symbol`: `:nonsymmetric` または `:symmetric`
  * `partition::Symbol`: `:column`、 `:row` または `:bidirectional`
  * `decompression::Symbol`: `:direct` または `:substitution`

# 適用可能なメソッド

  * [`column_colors`](@ref) と [`column_groups`](@ref) （`:column` または `:bidirectional` パーティションの場合）
  * [`row_colors`](@ref) と [`row_groups`](@ref) （`:row` または `:bidirectional` パーティションの場合）
  * [`sparsity_pattern`](@ref)
  * [`compress`](@ref)、[`decompress`](@ref)、[`decompress!`](@ref)、[`decompress_single_color!`](@ref)

!!! warning
    上記のメソッドとは異なり、`AbstractColoringResult` の具体的なサブタイプは公開APIの一部ではなく、予告なしに変更される可能性があります。

