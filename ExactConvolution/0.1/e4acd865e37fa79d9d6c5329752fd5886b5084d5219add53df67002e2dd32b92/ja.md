```
exact_conv([T,] a, b)
```

整数の配列 `a` と `b` を畳み込み、結果の配列を返します。

$$
exact\_conv(a,b)[k] = \sum_{i+j=k} a[i] \cdot b[j]
$$

# 注意事項:

  * 実装は、基盤となる DSP エンジンとして GMP の BigInt 乗算を使用しています（十分な入力に対しては FFT）。
  * T は結果をサポートするのに十分でなければなりません。
  * `a` と `b` に負の値を使用することはサポートされていますが、実行時の理由から推奨されません。

# 例

```jldoctest
julia> exact_conv(Int32, [1,2], [4,5,6])
4-element Vector{Int32}:
  4
 13
 16
 12
```
