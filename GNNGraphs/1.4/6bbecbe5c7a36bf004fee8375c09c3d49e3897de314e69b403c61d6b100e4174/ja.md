```
DataStore([n, data])
DataStore([n,] k1 = x1, k2 = x2, ...)
```

特徴配列のためのコンテナです。オプションの引数 `n` は、データストアに含まれる各配列について `numobs(x) == n` を強制します。

構築時に、`data` はシンボルと配列のペアのイテラブルまたはキーワード引数として提供できます：

```jldoctest
julia> ds = DataStore(3, x = rand(Float32, 2, 3), y = rand(Float32, 3))
DataStore(3) with 2 elements:
  y = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds = DataStore(3, Dict(:x => rand(Float32, 2, 3), :y => rand(Float32, 3))); # 上記と同等
```

`DataStore` は辞書と名前付きタプルの両方に似たインターフェースを持っています。配列はインデックスまたはプロパティ構文を使用してアクセスおよび追加できます：

```jldoctest docstr_datastore
julia> ds = DataStore(x = ones(Float32, 2, 3), y = zeros(Float32, 3))
DataStore() with 2 elements:
  y = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds.x   # `ds[:x]` と同じ
2×3 Matrix{Float32}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> ds.z = zeros(Float32, 3)  # 新しい特徴配列 `z` を追加します。同じく `ds[:z] = rand(Float32, 3)` と同じ
3-element Vector{Float32}:
 0.0
 0.0
 0.0
```

`DataStore` は反復処理でき、`keys(ds)` および `values(ds)` を使用してキーと値にアクセスできます。`map(f, ds)` は関数 `f` を各特徴配列に適用します：

```jldoctest docstr_datastore
julia> ds2 = map(x -> x .+ 1, ds)
DataStore() with 3 elements:
  y = 3-element Vector{Float32}
  z = 3-element Vector{Float32}
  x = 2×3 Matrix{Float32}

julia> ds2.z
3-element Vector{Float32}:
 1.0
 1.0
 1.0
```
