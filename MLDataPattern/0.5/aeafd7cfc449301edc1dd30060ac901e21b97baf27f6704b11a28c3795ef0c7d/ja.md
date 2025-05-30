```
stratifiedobs([f], data, [p = 0.7], [shuffle = true], [obsdim], [rng]) -> Tuple
```

`data`を`p`の値に比例して複数の互いに排他的なサブセットに分割します。観測値は、置換なしの層化サンプリングを使用してデータのサブセットに割り当てられます。これらのサブセットは、最初の要素が`p`の最初の浮動小数点数で指定された`data`の観測値の割合を含むサブセットの`Tuple`として返されます。

例えば、`p`が`Float64`自体である場合、返り値は2つの要素（すなわちサブセット）を持つタプルになります。この場合、最初の要素には`p`で指定された観測値の割合が含まれ、2番目の要素には残りが含まれます。以下のコードでは、最初のサブセット`train`には約70%の観測値が含まれ、2番目のサブセット`test`には残りが含まれます。[`splitobs`](@ref)との主な違いは、`y`のクラス分布が`train`と`test`で積極的に保持されることです。

```julia
train, test = stratifiedobs(y, p = 0.7)
```

`p`が`Float64`のタプルである場合、追加のサブセットが作成されます。この例では、`train`には約50%の観測値が含まれ、`val`には約30%、`test`には残りの20%が含まれます。

```julia
train, val, test = stratifiedobs(y, p = (0.5, 0.3))
```

複数のデータ引数をタプルとして`stratifiedobs`を呼び出すことも可能で、すべての引数は同じ数の観測値を持っている必要があります。`data`がタプルである場合、タプルの最後の要素がターゲットを含むと見なされます。

```julia
train, test = stratifiedobs((X, y), p = 0.7)
(X_train,y_train), (X_test,y_test) = stratifiedobs((X, y), p = 0.7)
```

オプションのパラメータ`shuffle`は、結果のデータサブセットをシャッフルするかどうかを決定します。`false`の場合、サブセット内の観測値はラベルに従ってグループ化されます。

```julia
julia> y = ["a", "b", "b", "b", "b", "a"] # 2つの不均衡クラス
6-element Array{String,1}:
 "a"
 "b"
 "b"
 "b"
 "b"
 "a"

julia> train, test = stratifiedobs(y, p = 0.5, shuffle = false)
(String["b","b","a"],String["b","b","a"])
```

オプションのパラメータ`obsdim`は、`data`のタイプに対して観測値を示す次元を指定するために使用できます。詳細については`?ObsDim`を参照してください。

```julia
# one-of-kエンコーディングの2つの不均衡クラス
julia> X = [1 0; 1 0; 1 0; 1 0; 0 1; 0 1]
6×2 Array{Int64,2}:
 1  0
 1  0
 1  0
 1  0
 0  1
 0  1

julia> train, test = stratifiedobs(argmax, X, p = 0.5, obsdim = 1)
([1 0; 1 0; 0 1], [0 1; 1 0; 1 0])
```

オプションの（キーワード）パラメータ`rng`を使用すると、シャッフルに使用される乱数生成器を指定できます。これは再現可能な結果が望ましい場合に便利です。デフォルトでは、グローバルRNGが使用されます。詳細については、Juliaの標準ライブラリの`Random`を参照してください。

```jldoctest; setup = :(using MLDataPattern)
julia> using Random: MersenneTwister

julia> X = [1:6;]
6-element Array{Int64,1}:
 1
 2
 3
 4
 5
 6

julia> y = [:a, :b, :b, :b, :b, :a]
6-element Array{Symbol,1}:
 :a
 :b
 :b
 :b
 :b
 :a

julia> train, test = stratifiedobs((x, y), rng=MersenneTwister(42))
(([5, 3, 1, 4], [:b, :b, :a, :b]), ([2, 6], [:b, :a]))
```

この関数が機能するためには、`data`の型が[`nobs`](@ref)と[`getobs`](@ref)を実装している必要があります。例えば、以下のコードは`stratifiedobs`が`DataTable`で機能するようにします。

```julia
# DataTables.jlを機能させる
LearnBase.getobs(data::DataTable, i) = data[i,:]
StatsBase.nobs(data::DataTable) = nrow(data)
```

パラメータ`f`を使用して、与えられた`data`の各観測値からターゲットを抽出または取得する方法を指定できます。

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

julia> train, test = stratifiedobs(row->row[:Y], data, 0.5);

julia> getobs(train)
3×3 DataTables.DataTable
│ Row │ X1        │ X2          │ Y │
├─────┼───────────┼─────────────┼───┤
│ 1   │ 0.933372  │ 0.812814    │ b │
│ 2   │ 0.522172  │ 0.245457    │ b │
│ 3   │ 0.0997825 │ 0.000341996 │ a │

julia> getobs(test)
3×3 DataTables.DataTable
│ Row │ X1       │ X2        │ Y │
├─────┼──────────┼───────────┼───┤
│ 1   │ 0.504629 │ 0.722906  │ b │
│ 2   │ 0.226582 │ 0.0443222 │ a │
│ 3   │ 0.505208 │ 0.11202   │ b │
```

データサブセットに関する詳細は[`DataSubset`](@ref)を参照してください。

また、[`undersample`](@ref)、[`oversample`](@ref)、[`splitobs`](@ref)も参照してください。
