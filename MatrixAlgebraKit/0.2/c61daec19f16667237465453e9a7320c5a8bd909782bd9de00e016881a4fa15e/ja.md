```
MatrixAlgebraKit.findtruncated_sorted(values::AbstractVector, strategy::TruncationStrategy)
```

[`MatrixAlgebraKit.findtruncated`](@ref) と同様ですが、値が絶対値の逆順にソートされていると仮定します。ただし、この仮定はチェックされないため、そのようにソートされていない値を渡すと、予期しない結果を静かに返す可能性があります。これは、[`svd_trunc!`](@ref) のデフォルト実装で使用されます。
