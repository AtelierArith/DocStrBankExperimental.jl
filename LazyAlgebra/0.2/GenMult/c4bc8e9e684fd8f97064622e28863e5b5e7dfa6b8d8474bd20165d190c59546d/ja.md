# 遅延一般化行列-行列乗算

```julia
lgemm([α=1,] [transA='N',] A, [transB='N',] B, Nc=2) -> C
```

は `C = α*op(A)*op(B)` を生成します。ここで `op(A)` は `transA` が `'N'` の場合は `A`、`transA` が `'T'` の場合は `transpose(A)`、`transA` が `'C'` の場合は `adjoint(A)` です。同様に `op(B)` と `transB` に対しても適用されます。式 `op(A)*op(B)` は行列-行列乗算ですが、`op(A)` と `op(B)` の連続する次元をグループ化することによって解釈されます（説明については [`lgemv`](@ref) を参照してください）。引数 `Nc` は結果の次元数を指定します。

インプレースバージョンは次のように呼び出されます：

```julia
lgemm!([α=1,] [transA='N',] A,  [transB='N',] B, [β=0,] C) -> C
```

これは `C` の内容を `α*op(A)*op(B) + β*C` で上書きします。注意点として、`C` は `A` または `B` とエイリアスされてはいけません。

乗数 `α` と `β` は両方とも指定するか省略する必要があります。これらは任意のスカラー数値であることができますが、それぞれ `promote_eltype(A,B)` と `eltype(C)` に変換されるため、`InexactError` 例外がスローされる可能性があります。

関連情報: [`lgemv`](@ref), [`LinearAlgebra.BLAS.gemm`](@ref), [`LinearAlgebra.BLAS.gemm!`](@ref)。
