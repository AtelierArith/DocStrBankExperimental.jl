# 遅延一般化行列-ベクトル乗算

```julia
lgemv([α=1,] [tr='N',] A, x) -> y
```

は `y = α*op(A)*x` を生成します。ここで `op(A)` は `tr` が `'N'` の場合は `A`、`tr` が `'T'` の場合は `transpose(A)`、`tr` が `'C'` の場合は `adjoint(A)` です。式 `op(A)*x` は行列-ベクトル乗算ですが、`A` と `x` の連続する次元を次のようにグループ化して解釈します：

  * `tr` が `'N'` の場合、`x` の末尾の次元は `A` の次元と一致し、`A` の先頭の次元は結果 `y` の次元です；
  * `tr` が `'T'` または `'C'` の場合、`x` の先頭の次元は `A` の次元と一致し、`A` の末尾の次元は結果 `y` の次元です。

インプレースバージョンは次のように呼び出されます：

```julia
lgemv!([α=1,] [tr='N',] A, x, [β=0,] y) -> y
```

これは `y` の内容を `α*op(A)*x + β*y` で上書きします。`x` と `y` はエイリアスであってはならないことに注意してください。

乗数 `α` と `β` は両方とも指定するか省略する必要があり、任意のスカラー数であることができますが、それぞれ `promote_eltype(A,x)` と `eltype(y)` に変換され、`InexactError` 例外をスローする可能性があります。

関連情報: [`lgemm`](@ref), [`LinearAlgebra.BLAS.gemv`](@ref), [`LinearAlgebra.BLAS.gemv!`](@ref)。
