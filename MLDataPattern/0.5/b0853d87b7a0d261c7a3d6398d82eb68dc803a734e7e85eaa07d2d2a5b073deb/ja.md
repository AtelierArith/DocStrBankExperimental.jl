```
BatchView(data, [size|maxsize], [count], [obsdim])
```

# 説明

与えられた `data` のビューを作成し、それをバッチのベクトルとして表現します。各バッチには同じ数の観測が含まれます。バッチの数とバッチサイズは、(キーワード) パラメータ `count` と `size` を使用して指定できます。データセットのサイズが指定された (または推測された) `size` で割り切れない場合、残りの観測は警告とともに無視されます。

データアクセスは `getindex` が呼ばれるまで遅延され、さらに `getindex` は一般的にデータの移動を避ける [`datasubset`](@ref) の結果を返します。これは、[`getobs`](@ref) が呼ばれるまで続きます。

イテレータとして使用される場合、オブジェクトはデータセットを一度だけ反復し、実質的にエポックを示します。各反復は一定の [`nobs`](@ref) のミニバッチを返し、これにより [`data`](@ref) を一度に1バッチずつ反復することができます。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`getobs`(@ref) と `nobs`(@ref) を実装している限り、任意の型で構いません（詳細については詳細を参照してください）。
  * **`size`** : 各バッチのバッチサイズ。すなわち、各バッチが含むべき観測の数。
  * **`maxsize`** : 各バッチの最大バッチサイズ。すなわち、各バッチが含むべき観測の数。総観測数がサイズで割り切れない場合、サイズが割り切れるまで減少します。
  * **`count`** : ビューが含むバッチの数。
  * **`obsdim`** : オプション。`data` の型に意味がある場合、`obsdim` を使用して `data` のどの次元が観測を示すかを指定できます。型安定な方法で位置引数として指定することもできます（`?LearnBase.ObsDim` を参照）、またはより便利にスマートキーワード引数として指定できます。

# メソッド

`AbstractArray` インターフェースに加えて、以下の追加メソッドが提供されます。

  * **`getobs(data::BatchView, batchindices)`** : `batchindices` で指定されたバッチの `Vector` を返します。
  * **`nobs(data::BatchView)`** : `data` の総観測数を返します。バッチサイズが1でない限り、この数は `length` とは異なることに注意してください。

# 詳細

`BatchView` がデータ構造で機能するためには、与えられた変数 `data` の型がデータコンテナインターフェースを実装している必要があります。詳細については `?DataSubset` を参照してください。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```julia
using MLDataUtils
X, Y = MLDataUtils.load_iris()

A = batchview(X, size = 30)
@assert typeof(A) <: BatchView <: AbstractVector
@assert eltype(A) <: SubArray{Float64,2}
@assert length(A) == 5 # アイリスには150の観測があります
@assert size(A[1]) == (4,30) # アイリスには4つの特徴があります

# 30観測の5バッチ
for x in batchview(X, size = 30)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert nobs(x) === 30
end

# 20観測の7バッチ
# アイリスデータセットには150の観測があることに注意してください。
# つまり、バッチサイズが20の場合、最後の
# 10の観測は無視されます
for (x,y) in batchview((X,Y), size = 20)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert nobs(x) === nobs(y) === 20
end

# 15観測の10バッチ
for (x,y) in batchview((X,Y), maxsize = 20)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert nobs(x) === nobs(y) === 15
end

# 観測を1つのバッチにのみランダムに割り当てます。
for (x,y) in batchview(shuffleobs((X,Y)))
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
end

# 各15観測の最初の2バッチを反復します
for (x,y) in batchview((X,Y), size=15, count=2)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
    @assert size(x) == (4, 15)
    @assert size(y) == (15,)
end
```

# 参照

[`eachbatch`](@ref), [`ObsView`](@ref), [`shuffleobs`](@ref), [`getobs`](@ref), [`nobs`](@ref), [`DataSubset`](@ref)
