```
ObsView(data, [obsdim])
```

# 説明

与えられた `data` の個々の観測のベクトルの形でビューを作成します。データアクセスは `getindex` が呼ばれるまで遅延され、さらに `getindex` は一般的にデータの移動を避ける [`datasubset`](@ref) の結果を返します。これは [`getobs`](@ref) が呼ばれるまで続きます。

イテレータとして使用される場合、ビューはデータセットを一度だけ反復処理し、実質的にエポックを示します。各反復は現在の観測に対する遅延サブセットを返します。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`getobs`](@ref) と [`nobs`](@ref) を実装している限り、任意の型で構いません（詳細については詳細を参照してください）。
  * **`obsdim`** : オプション。`data` の型に意味がある場合、`obsdim` を使用して `data` のどの次元が観測を示すかを指定できます。位置引数として型安定な方法で指定することもできます（`?LearnBase.ObsDim` を参照）、またはスマートキーワード引数としてより便利に指定できます。

# メソッド

`AbstractArray` インターフェースに加えて、以下の追加メソッドが提供されています：

  * **`getobs(data::ObsView, indices::AbstractVector)`** : `indices` で指定された個々の観測の `Vector` を返します。
  * **`nobs(data::ObsView)`** : イテレータが処理する `data` の観測の数を返します。

# 詳細

`ObsView` が特定のデータ構造で機能するためには、与えられた変数 `data` の型がデータコンテナインターフェースを実装している必要があります。詳細については `?DataSubset` を参照してください。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```julia
X, Y = MLDataUtils.load_iris()

A = obsview(X)
@assert typeof(A) <: ObsView <: AbstractVector
@assert eltype(A) <: SubArray{Float64,1}
@assert length(A) == 150 # アイリスには150の観測があります
@assert size(A[1]) == (4,) # アイリスには4つの特徴があります

for x in obsview(X)
    @assert typeof(x) <: SubArray{Float64,1}
end

# 各個別のラベル付き観測を反復処理
for (x,y) in obsview((X,Y))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end

# 同じだがランダムな順序で
for (x,y) in obsview(shuffleobs((X,Y)))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end
```

# 参照

[`eachobs`](@ref), [`BatchView`](@ref), [`shuffleobs`](@ref), [`getobs`](@ref), [`nobs`](@ref), [`DataSubset`](@ref)
