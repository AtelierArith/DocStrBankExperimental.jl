```
DimStack <: AbstractDimStack

DimStack(data::AbstractDimArray...)
DimStack(data::Tuple{Vararg{AbstractDimArray}})
DimStack(data::NamedTuple{Keys,Vararg{AbstractDimArray}})
DimStack(data::NamedTuple, dims::DimTuple; metadata=NoMetadata())
```

DimStackは、`NamedTuple`内でいくつかの次元を共有する複数のオブジェクトを保持します。

特に、彼らの動作は`DimArray`と`NamedTuple`の間に位置しています：

  * `dimstack[:symbol]`のように`Symbol`でインデックスを付けると、`DimArray`のレイヤーが返されます。
  * 繰り返し処理や`map`は、`Symbol`でインデックスを付けた配列レイヤーに適用されます。
  * `Int`、`Dimension`、または`Int`に解決される`Selector`を使った`getindex`または`view`は、スタック内の各レイヤーからの値の`NamedTuple`を返します。これは非常に良いパフォーマンスを持ち、常に`map`を使用する必要を回避します。
  * `Vector`または`Colon`を使った`getindex`または`view`は、すべてのデータレイヤーがスライスされた別の`DimStack`を返します。
  * `setindex!`は、レイヤーに一致する`Tuple`または`NamedTuple`を渡す必要があります。
  * 多くの基本的な`Statistics`メソッド（`sum`、`mean`など）は、`DimArray`と同様に機能し、再び`map`を使用する必要を取り除きます。

例えば、ここではすべてのレイヤーに対して時間次元の平均を取ります：

```julia
mean(mydimstack; dims=Ti)
```

これは次のように等価です：

```julia
map(A -> mean(A; dims=Ti), mydimstack)
```

この設計は、多層の混合次元オブジェクトを扱う際に簡潔なコードを提供します。

しかし、最初は驚くかもしれません - 最も驚くべき結果は、`dimstack[1]`がすべてのレイヤーの最初のインデックスの値の`NamedTuple`を返すのに対し、`first(dimstack)`はイテレータの最初の値、すなわち最初のレイヤーの`DimArray`を返すことです。

`DimStack`は、複数の`AbstractDimArray`または`AbstractArray`の`NamedTuple`と一致する`dims`タプルから構築できます。

`AbstractArray`に適用されるほとんどの`Base`および`Statistics`メソッドは、スタックのすべてのレイヤーに同時に使用できます。その結果は`DimStack`であり、`mean`のようなメソッドが`dims`引数なしで使用されると、単一の非配列値を返す`NamedTuple`になります。

## 例

```jldoctest
julia> using DimensionalData

julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0];

julia> dimz = (X([:a, :b]), Y(10.0:10.0:30.0))
X Symbol[:a, :b],
Y 10.0:10.0:30.0

julia> da1 = DimArray(1A, dimz; name=:one);

julia> da2 = DimArray(2A, dimz; name=:two);

julia> da3 = DimArray(3A, dimz; name=:three);

julia> s = DimStack(da1, da2, da3);

julia> s[At(:b), At(10.0)]
(one = 4.0, two = 8.0, three = 12.0)

julia> s[X(At(:a))] isa DimStack
true
```
