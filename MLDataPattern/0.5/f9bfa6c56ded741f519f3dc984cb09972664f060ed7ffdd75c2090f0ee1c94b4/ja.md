```
RandomObs(data, [count], [obsdim])
```

# 説明

`data` から `count` のランダムにサンプリングされた観測値を生成するイテレータを作成します。`count` が指定されていない場合、無限にランダムサンプルを生成します。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`getobs`[@ref] と `nobs`[@ref] を実装している限り、任意の型で構いません（詳細については、詳細を参照してください）。
  * **`count`** : オプション。イテレータが停止する前に生成するランダムにサンプリングされた観測値の数。省略すると、イテレータは無限にランダムにサンプリングされた観測値を生成します。
  * **`obsdim`** : オプション。`data` の型に意味がある場合、`obsdim` を使用して `data` のどの次元が観測値を示すかを指定できます。位置引数として型安定な方法で指定することもできます（`?LearnBase.ObsDim` を参照）、またはスマートキーワード引数としてより便利に指定できます。

# 詳細

`RandomObs` が特定のデータ構造で機能するためには、与えられた変数 `data` の型がデータコンテナインターフェースを実装している必要があります。詳細については `?DataSubset` を参照してください。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```julia
X, Y = MLDataUtils.load_iris()

# X から 500 のランダムにサンプリングされた観測値を取得
i = 0
for x in RandomObs(X, 500) # または: RandomObs(X, count = 500)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert length(x) == 4
    i += 1
end
@assert i == 500

# count が指定されていない場合、イテレータは無限にサンプルを生成します
for x in RandomObs(X)
    # このループは break が使用されない限り決して停止しません
    if true; break; end
end

# 複数のデータ引数（例: ラベル付きデータ）にも対応
for (x,y) in RandomObs((X,Y), count = 100)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end
```

# 参照

[`BalancedObs`](@ref), [`RandomBatches`](@ref), [`ObsView`](@ref), [`BatchView`](@ref), [`shuffleobs`](@ref), [`DataSubset`](@ref), [`BufferGetObs`](@ref)
