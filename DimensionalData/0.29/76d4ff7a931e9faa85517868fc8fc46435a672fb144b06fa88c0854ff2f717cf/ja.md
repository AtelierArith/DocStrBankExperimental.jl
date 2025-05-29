```
DimStack <: AbstractDimStack

DimStack(data::AbstractDimArray...; kw...)
DimStack(data::Union{AbstractArray,Tuple,NamedTuple}, [dims::DimTuple]; kw...)
DimStack(data::AbstractDimArray; layersfrom, kw...)
```

DimStackは、`NamedTuple`内でいくつかの次元を共有する複数のオブジェクトを保持します。

## 引数

  * `data`: `AbstractDimArray`または`AbstractArray`、`Tuple`または`NamedTuple`の`AbstractDimArray`または`AbstractArray`の集合。
  * `dims`: `Dimension`の`DimTuple`。`data`が`AbstractDimArray`でない場合に必要です。

## キーワード

  * `name`: 各レイヤーのための`Symbol`名の`Array`または`Tuple`。デフォルトでは、`DimArrays`の名前または`NamedTuple`のキーが使用され、`:layer1`、`:layer2`などになります。
  * `metadata`: スタックのための`AbstractDict`または`NamedTuple`のメタデータ。
  * `layersfrom`: データが単一の`DimArray`の場合にレイヤーをスライスするための次元。デフォルトは`nothing`です。

（これらは高度な使用のためのものです）

  * `layerdims`: 各レイヤーの次元に一致させるための次元タプルの`Array`、`Tuple`または`NamedTuple`。`layerdims`の次元は`dims`にも含まれている必要があります。
  * `layermetadata`: 各レイヤーのためのメタデータの`Array`、`Tuple`または`NamedTuple`。
  * `refdims`: 各レイヤーのための`Dimension`の`NamedTuple`。デフォルトは`()`です。

## 詳細

`DimStack`の動作は、`DimArray`と`NamedTuple`の間にあります：

  * `Symbol`を使ったインデクシング（例：`dimstack[:layername]`）や`getproperty`を使用すると、`DimArray`レイヤーが返されます（例：`dimstack.layername`）。
  * `DimStack`は、各レイヤーの値に対応する`NamedTuple`を反復処理します。これは、`map`、`broadcast`、`collect`のような関数が、`DimStack`が`DimArray{<:NamedTuple}`であるかのように動作することを意味します。
  * `getindex`または`view`を`Vector`または`Colon`で使用すると、すべてのデータレイヤーがスライスされた別の`DimStack`が返されます。ただし、これが単一の要素に解決される場合、`getindex`は`NamedTuple`を返します。
  * `setindex!`は、レイヤーに一致する`Tuple`または`NamedTuple`を渡す必要があります。
  * 多くの基本的なメソッドや`Statistics`メソッド（`sum`、`mean`など）は、`DimArray`に対して行われるように、すべてのレイヤーに個別に適用されます。
  * `DimStack`の各レイヤーに関数を適用するには、[`maplayers`](@ref)を使用します。

```julia
function DimStack(A::AbstractDimArray;
    layersfrom=nothing, name=nothing, metadata=metadata(A), refdims=refdims(A), kw...
)
```

例えば、ここではすべてのレイヤーに対して時間次元に沿って平均を取ります：

```julia
mean(mydimstack; dims=Ti)
```

これは次のように等価です：

```julia
maplayers(A -> mean(A; dims=Ti), mydimstack)
```

この設計は、多層の混合次元オブジェクトを扱う際に簡潔なコードを提供します。

しかし、最初は驚くかもしれません - 最も驚くべき結果は、`dimstack[1]`がすべてのレイヤーの最初のインデックスの値の`NamedTuple`を返すのに対し、`first(dimstack)`はイテレータの最初の値、すなわち最初のレイヤーの`DimArray`を返すことです。

`DimStack`は、複数の`AbstractDimArray`または`AbstractArray`の`NamedTuple`と一致する`dims`タプルから構築できます。

`AbstractArray`に適用されるほとんどの`Base`および`Statistics`メソッドは、スタックのすべてのレイヤーに同時に使用できます。結果は`DimStack`であり、`mean`のようなメソッドが`dims`引数なしで使用されると、単一の非配列値を返す`NamedTuple`になります。

## 例

```jldoctest
julia> using DimensionalData

julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0];

julia> dimz = (X([:a, :b]), Y(10.0:10.0:30.0))
(↓ X [:a, :b],
→ Y 10.0:10.0:30.0)

julia> da1 = DimArray(1A, dimz; name=:one);

julia> da2 = DimArray(2A, dimz; name=:two);

julia> da3 = DimArray(3A, dimz; name=:three);

julia> s = DimStack(da1, da2, da3);

julia> s[At(:b), At(10.0)]
(one = 4.0, two = 8.0, three = 12.0)

julia> s[X(At(:a))] isa DimStack
true
```
