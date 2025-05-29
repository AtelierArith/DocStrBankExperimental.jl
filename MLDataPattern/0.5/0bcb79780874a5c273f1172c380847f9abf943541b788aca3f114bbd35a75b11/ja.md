```
BalancedObs([f], data, [count], [obsdim])
```

# 説明

`data` から `count` のランダムにサンプリングされた観測値を生成するイテレータを作成します。`count` が指定されていない場合、無限にランダムサンプルを生成します。

[`RandomObs`](@ref) とは異なり、`BalancedObs` は `data` がラベル付きデータコンテナであることを期待します。`data` のラベル分布を使用して、すべてのラベルがサンプリングされる確率が等しくなるようにします。

# 引数

  * **`f`** : オプション。各観測値に個別に適用されるべき関数で、その観測値のターゲットを抽出または計算するために使用されます。この関数は、各観測値がどのラベルに属するかを決定するために、構築時に一度だけ使用されます。
  * **`data`** : データセットを説明するオブジェクト。`getobs`(@ref)、`nobs`(@ref)、およびオプションで `gettargets`(@ref) を実装している限り、任意のタイプで構いません（詳細については詳細を参照してください）。
  * **`count`** : オプション。イテレータが停止する前に生成するランダムにサンプリングされた観測値の数。省略すると、イテレータは無限にランダムにサンプリングされた観測値を生成します。
  * **`obsdim`** : オプション。`data` のタイプに意味がある場合、`obsdim` を使用して `data` のどの次元が観測値を示すかを指定できます。位置引数として型安定な方法で指定することもできます（`?LearnBase.ObsDim` を参照）、またはスマートキーワード引数としてより便利に指定できます。

# 詳細

`BalancedObs` が特定のデータ構造で機能するためには、与えられた変数 `data` の型がラベル付きデータコンテナインターフェースを実装している必要があります。詳細については `?DataSubset` を参照してください。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)

# 例

```julia
# iris データの最初の 55 観測値を例として読み込む
# - "setosa" のための 50 観測値
# - "versicolor" のための 5 観測値
X, Y = MLDataUtils.load_iris(55)

# X で 100 のバランスの取れたサンプル観測値を取得する
num_versicolor = 0
for (x,y) in BalancedObs((X,Y), 100) # または: BalancedObs((X,Y), count = 100)
    @assert typeof(x) <: SubArray{Float64,1}
    @assert length(x) == 4
    # versicolor の観測値を何回サンプリングしたかをカウントする
    num_versicolor += y[] == "versicolor" ? 1 : 0
end
println(num_versicolor) # 約 50

# count が指定されていない場合、イテレータは無限にサンプルを生成します
for (x,y) in BalancedObs((X,Y))
    # このループは break が使用されない限り決して停止しません
    if true; break; end
end
```

# 参照

[`RandomObs`](@ref)、[`targets`](@ref)、[`RandomBatches`](@ref)、[`ObsView`](@ref)、[`BatchView`](@ref)、[`shuffleobs`](@ref)、[`DataSubset`](@ref)、[`BufferGetObs`](@ref)
