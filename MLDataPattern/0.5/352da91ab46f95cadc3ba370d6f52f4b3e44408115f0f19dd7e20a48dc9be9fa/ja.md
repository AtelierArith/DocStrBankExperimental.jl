```
RandomBatches(data, [size], [count], [obsdim])
```

# 説明

`data` から `count` 個のランダムにサンプリングされたバッチを生成するイテレータを作成します。バッチサイズは `size` です。`count` が指定されていない場合、ランダムバッチを無限に生成します。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`getobs`(@ref) と `nobs`(@ref) を実装している限り、任意の型で構いません（詳細については、詳細を参照してください）。
  * **`size`** : オプション。各バッチのバッチサイズ。すなわち、各バッチにおけるランダムにサンプリングされた観測の数。
  * **`count`** : オプション。イテレータが停止する前に生成するランダムにサンプリングされたバッチの数。省略した場合、イテレータは無限にランダムにサンプリングされたバッチを生成します。
  * **`obsdim`** : オプション。`data` の型に意味がある場合、`obsdim` を使用して `data` のどの次元が観測を示すかを指定できます。位置引数として型安定な方法で指定することもできます（`?LearnBase.ObsDim` を参照）、またはスマートキーワード引数としてより便利に指定できます。

# 詳細

`RandomBatches` が特定のデータ構造で機能するためには、与えられた変数 `data` の型がデータコンテナインターフェースを実装している必要があります。詳細については `?DataSubset` を参照してください。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```julia
X, Y = MLDataUtils.load_iris()

# バッチサイズ10の500個のランダムにサンプリングされたバッチを処理する
i = 0
for x in RandomBatches(X, 10, 500) # または: RandomObs(X, size = 10, count = 500)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert size(x) == (4,10)
    i += 1
end
@assert i == 500

# count が指定されていない場合、イテレータは無限にサンプルを生成します
for x in RandomBatches(X, 10)
    # このループは break が使用されない限り決して停止しません
    if true; break; end
end

# 複数のデータ引数（例: ラベル付きデータ）にも対応
for (x,y) in RandomBatches((X,Y), 10, 500)
    @assert typeof(x) <: SubArray{Float64,2}
    @assert typeof(y) <: SubArray{String,1}
end
```

# 参照

[`RandomObs`](@ref), [`BatchView`](@ref), [`ObsView`](@ref), [`shuffleobs`](@ref), [`DataSubset`](@ref), [`BufferGetObs`](@ref)
