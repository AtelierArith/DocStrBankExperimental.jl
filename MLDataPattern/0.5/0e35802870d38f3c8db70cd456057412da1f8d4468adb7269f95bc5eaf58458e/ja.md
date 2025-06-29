```
undersample([f], data, [shuffle = false], [obsdim])
```

`data`の観測値をサブサンプリングすることによって、クラスバランスの取れたバージョンを生成します。これにより、結果として得られる観測値の数はすべてのクラスで同じになります。この方法では、すべてのクラスが、与えられた（元の）`data`の中で最も小さいクラスが持つ観測値の数と同じだけの観測値を持つことになります。

便利なパラメータ`shuffle`は、生成されたデータが作成後にシャッフルされるかどうかを決定します。シャッフルされない場合、すべての観測値は元の順序のままになります。デフォルトは`false`です。

オプションのパラメータ`obsdim`は、`data`のタイプに対して観測値を示す次元を指定するために使用できます。詳細については`?ObsDim`を参照してください。

```julia
# 6つの観測値とそれぞれ3つの特徴
X = rand(3, 6)
# 2つのクラス、非常に不均衡
Y = ["a", "b", "b", "b", "b", "a"]

# クラス"b"を" a"に合わせてサブサンプリング
X_bal, Y_bal = undersample((X,Y))

# これにより、より小さなデータセットが得られます
@assert size(X_bal) == (3,4)
@assert length(Y_bal) == 4

# これで" a"と" b"の両方がそれぞれ2つの観測値を持つことになります
@assert sum(Y_bal .== "a") == 2
@assert sum(Y_bal .== "b") == 2
```

この関数が機能するためには、`data`のタイプが[`nobs`](@ref)と[`getobs`](@ref)を実装している必要があります。たとえば、次のコードは`undersample`が`DataTable`で機能するようにします。

```julia
# DataTables.jlを機能させる
LearnBase.getobs(data::DataTable, i) = data[i,:]
StatsBase.nobs(data::DataTable) = nrow(data)
```

パラメータ`f`を使用して、与えられた`data`の各観測値からターゲットを抽出または取得する方法を指定できます。`data`がタプルである場合、タプルの最後の要素にターゲットが含まれていると見なされ、その要素内の各観測値に`f`が適用されます。

```julia
julia> data = DataTable(Any[rand(6), rand(6), [:a,:b,:b,:b,:b,:a]], [:X1,:X2,:Y])
6×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.226582  │ 0.0443222   │ a │
│ 2   │ 0.504629  │ 0.722906    │ b │
│ 3   │ 0.933372  │ 0.812814    │ b │
│ 4   │ 0.522172  │ 0.245457    │ b │
│ 5   │ 0.505208  │ 0.11202     │ b │
│ 6   │ 0.0997825 │ 0.000341996 │ a │

julia> getobs(undersample(row->row[:Y], data))
4×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.226582  │ 0.0443222   │ a │
│ 2   │ 0.504629  │ 0.722906    │ b │
│ 3   │ 0.522172  │ 0.245457    │ b │
│ 4   │ 0.0997825 │ 0.000341996 │ a │
```

データサブセットに関する詳細は[`DataSubset`](@ref)を参照してください。

また、[`oversample`](@ref)および[`stratifiedobs`](@ref)も参照してください。
