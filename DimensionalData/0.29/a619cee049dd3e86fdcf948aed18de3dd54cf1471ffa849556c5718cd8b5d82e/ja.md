```
@d broadcast_expression options
```

次元ブロードキャストマクロは、Base Juliaのブロードキャスティングを拡張して、欠損値や順序が変更された次元で動作します。

すべての [`AbstractDimArray`](@ref) が一致する次元でブロードキャストされるように、単一の次元を順序変更および再形成します。

マクロの第二引数としてオプションを渡すことで、動作を制御することが可能です。これは単一の代入またはNamedTupleとして渡すことができます。オプション名は明示的に記述する必要があり、namedtuple変数として渡すことはできません。

# オプション

  * `dims`: 出力配列の次元順序を固定するために、`Dimension`、`Dimension`型、または`Symbol`のタプルを渡します。そうでなければ、次元は出現順に配置されます。ルックアップを伴うdimsが渡された場合、これらは`set`を使って返される配列に適用されます。
  * `strict`: `true`または`false`。すべてのルックアップ値が明示的に一致するかどうかを確認します。

他のすべてのキーワードは`DimensionalData.rebuild`に渡されます。これは、返される配列の`name`、`metadata`などをここで設定できることを意味します。また、例えば`Rasters.jl`の`missingval`なども設定できます。

# 例

```julia
using DimensionalData
da1 = ones(X(3))
da2 = fill(2, Y(4), X(3))

@d da1 .* da2
@d da1 .* da2 .+ 5 dims=(Y, X)
@d da1 .* da2 .+ 5 (dims=(Y, X), strict=false, name=:testname)
```

## `@.`との併用

`@d`は`@.`を暗示しません。各ブロードキャストを指定する必要があります。しかし、`@.`は`@d`の*内部*マクロとして使用できます。

```julia
using DimensionalData
da1 = ones(X(3))
da2 = fill(2, Y(4), X(3))

@d @. da1 * da2
# オプションを渡す必要がある場合は、`@.`の周りに括弧を使用します
@d (@. da1 * da2 .+ 5) dims=(Y, X)
```
