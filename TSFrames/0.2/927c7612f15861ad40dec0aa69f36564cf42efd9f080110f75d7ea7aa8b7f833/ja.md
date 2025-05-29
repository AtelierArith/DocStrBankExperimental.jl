```
struct TSFrame
  coredata :: DataFrame
end
```

`::TSFrame` - インデックス付きの順序データを保持するための型。

TSFrameオブジェクトは、本質的に特定の列がインデックスとしてマークされた[DataFrame](https://dataframes.juliadata.org/)です。最初の引数には、DataFrame、Vector、または2次元のArrayを受け入れることができます。また、[Tables.jl](https://github.com/JuliaData/Tables.jl)互換のテーブルも入力として受け入れられます。

最初の引数が`DataFrame`の場合、DataFrameにはインデックス列も含まれている可能性があります。インデックス列は、2番目の引数`index`として列番号または列名を`String`または`Symbol`で提供することによって特定できます。

DataFrameにインデックス列が存在しない場合、連続したインデックスが自動的に作成されます。

入力された`DataFrame`は構築中にソートされ、プロパティ`coredata`に保存されます。インデックスは`coredata` DataFrameの`Index`という列に保存されます。このインデックスは[`index()`](@ref)メソッドを使用して取得できます。

コンストラクタに空のDataFrameを提供すると、空のインデックスと列のないTSFrameオブジェクトが生成されます。同様に、最初の引数として空のVectorまたは空のArrayを提供すると、列のない空のTSFrameが生成されます。

コンストラクタに許可されるデータ入力は`DataFrame`、`Vector`、および2次元の`Array`です。

`TSFrame(coredata::DataFrame)`: ここでは、コンストラクタは`coredata`内に`Index`という名前の列をインデックス列として探します。これが見つからない場合、デフォルトで`coredata`の最初の列がインデックスとして設定されます。`coredata`に列が1つしかない場合、新しい連続インデックスが生成されます。

`TSFrame.coredata`はDataFrameであるため、DataFramesパッケージによって提供されるメソッド（例：`transform`、`combine`など）を使用して独立して操作できます。

# コンストラクタ

```julia
TSFrame(coredata::DataFrame, index::Union{String, Symbol, Int}; issorted = false, copycols = true)
TSFrame(coredata::DataFrame, index::AbstractVector{T}; issorted = false, copycols = true) where {T<:Union{Int, TimeType}}
TSFrame(coredata::DataFrame; issorted = false, copycols = true)
TSFrame(coredata::DataFrame, index::UnitRange{Int}; issorted = false, copycols = true)
TSFrame(coredata::AbstractVector{T}, index::AbstractVector{V}; colnames=:auto, issorted = false, copycols = true) where {T, V}
TSFrame(coredata::AbstractVector{T}; colnames=:auto, issorted = false, copycols = true) where {T}
TSFrame(coredata::AbstractArray{T,2}; colnames=:auto, issorted = false, copycols = true) where {T}
TSFrame(coredata::AbstractArray{T,2}, index::AbstractVector{V}; colnames=:auto, issorted = false, copycols = true) where {T, V}
TSFrame(IndexType::DataType; n::Int=1)
TSFrame(IndexType::DataType, cols::Vector{Tuple{DataType, S}}; issorted = false, copycols = true) where S <: Union{Symbol, String}
```

`issorted`が`true`の場合、入力に対してソート操作は行われません。`copycols`が`true`の場合、入力はコピーされず、TSFrameに直接配置されます。これは危険な場合があるため、入力配列が後で変更されない場合にのみ`false`に設定してください。

`issorted = true, copycols = false`は、特にループや他のパフォーマンスに敏感なコードでTSFrameを構築する際にパフォーマンスの利点を提供します。

# 例

```jldoctest; setup = :(using TSFrames, DataFrames, Dates, Random, Statistics)
julia> using Random;
julia> random(x) = rand(MersenneTwister(123), x);

julia> df = DataFrame(x1 = random(10))
10×1 DataFrame
 Row │ x1
     │ Float64
─────┼───────────
   1 │ 0.768448
   2 │ 0.940515
   3 │ 0.673959
   4 │ 0.395453
   5 │ 0.313244
   6 │ 0.662555
   7 │ 0.586022
   8 │ 0.0521332
   9 │ 0.26864
  10 │ 0.108871

julia> ts = TSFrame(df)   # インデックスを生成
(10 x 1) TSFrame with Int64 Index

 Index  x1
 Int64  Float64
──────────────────
     1  0.768448
     2  0.940515
     3  0.673959
     4  0.395453
     5  0.313244
     6  0.662555
     7  0.586022
     8  0.0521332
     9  0.26864
    10  0.108871

# ts.coredataはDataFrameです
julia> combine(ts.coredata, :x1 => Statistics.mean, DataFrames.nrow)
1×2 DataFrame
 Row │ x1_mean  nrow
     │ Float64  Int64
─────┼────────────────
   1 │ 0.49898    418

julia> df = DataFrame(ind = [1, 2, 3], x1 = random(3))
3×2 DataFrame
 Row │ ind    x1
     │ Int64  Float64
─────┼─────────────────
   1 │     1  0.768448
   2 │     2  0.940515
   3 │     3  0.673959

julia> ts = TSFrame(df, 1)        # 最初の列がインデックス
(3 x 1) TSFrame with Int64 Index

 Index  x1
 Int64  Float64
─────────────────
     1  0.768448
     2  0.940515
     3  0.673959

julia> df = DataFrame(x1 = random(3), x2 = random(3), Index = [1, 2, 3]);
3×3 DataFrame
 Row │ x1        x2        Index
     │ Float64   Float64   Int64
─────┼───────────────────────────
   1 │ 0.768448  0.768448      1
   2 │ 0.940515  0.940515      2
   3 │ 0.673959  0.673959      3

julia> ts = TSFrame(df)   # 既存の`Index`列を使用
(3 x 2) TSFrame with Int64 Index

 Index  x1        x2
 Int64  Float64   Float64
───────────────────────────
     1  0.768448  0.768448
     2  0.940515  0.940515
     3  0.673959  0.673959

julia> dates = collect(Date(2017,1,1):Day(1):Date(2017,1,10));

julia> df = DataFrame(dates = dates, x1 = random(10))
10×2 DataFrame
 Row │ dates       x1
     │ Date        Float64
─────┼───────────────────────
   1 │ 2017-01-01  0.768448
   2 │ 2017-01-02  0.940515
   3 │ 2017-01-03  0.673959
   4 │ 2017-01-04  0.395453
   5 │ 2017-01-05  0.313244
   6 │ 2017-01-06  0.662555
   7 │ 2017-01-07  0.586022
   8 │ 2017-01-08  0.0521332
   9 │ 2017-01-09  0.26864
  10 │ 2017-01-10  0.108871

julia> ts = TSFrame(df, :dates)
(10 x 1) TSFrame with Date Index

 Index       x1
 Date        Float64
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871

julia> ts = TSFrame(DataFrame(x1=random(10)), dates);

julia> ts = TSFrame(random(10))
(10 x 1) TSFrame with Int64 Index

 Index  x1
 Int64  Float64
──────────────────
     1  0.768448
     2  0.940515
     3  0.673959
     4  0.395453
     5  0.313244
     6  0.662555
     7  0.586022
     8  0.0521332
     9  0.26864
    10  0.108871

julia> ts = TSFrame(random(10), colnames=[:A]) # 列はAと名付けられます
(10 x 1) TSFrame with Int64 Index

 Index  A
 Int64  Float64
──────────────────
     1  0.768448
     2  0.940515
     3  0.673959
     4  0.395453
     5  0.313244
     6  0.662555
     7  0.586022
     8  0.0521332
     9  0.26864
    10  0.108871

julia> ts = TSFrame(random(10), dates)
(10 x 1) TSFrame with Date Index

 Index       x1        
 Date        Float64   
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871

julia> ts = TSFrame(random(10), dates, colnames=[:A]) # 列はAと名付けられます
(10 x 1) TSFrame with Date Index

 Index       A         
 Date        Float64   
───────────────────────
 2017-01-01  0.768448
 2017-01-02  0.940515
 2017-01-03  0.673959
 2017-01-04  0.395453
 2017-01-05  0.313244
 2017-01-06  0.662555
 2017-01-07  0.586022
 2017-01-08  0.0521332
 2017-01-09  0.26864
 2017-01-10  0.108871

julia> ts = TSFrame([random(10) random(10)]) # 行列オブジェクト
(10 x 2) TSFrame with Int64 Index

 Index  x1         x2        
 Int64  Float64    Float64   
─────────────────────────────
     1  0.768448   0.768448
     2  0.940515   0.940515
     3  0.673959   0.673959
     4  0.395453   0.395453
     5  0.313244   0.313244
     6  0.662555   0.662555
     7  0.586022   0.586022
     8  0.0521332  0.0521332
     9  0.26864    0.26864
    10  0.108871   0.108871

julia> ts = TSFrame([random(10) random(10)], colnames=[:A, :B]) # 列はAとBと名付けられます
(10 x 2) TSFrame with Int64 Index

 Index  A          B       
 Int64  Float64    Float64   
─────────────────────────────
     1  0.768448   0.768448
     2  0.940515   0.940515
     3  0.673959   0.673959
     4  0.395453   0.395453
     5  0.313244   0.313244
     6  0.662555   0.662555
     7  0.586022   0.586022
     8  0.0521332  0.0521332
     9  0.26864    0.26864
    10  0.108871   0.108871

julia> ts = TSFrame([random(10) random(10)], dates) 
(10 x 2) TSFrame with Date Index

 Index       x1         x2
 Date        Float64    Float64
──────────────────────────────────
 2017-01-01  0.768448   0.768448
 2017-01-02  0.940515   0.940515
 2017-01-03  0.673959   0.673959
 2017-01-04  0.395453   0.395453
 2017-01-05  0.313244   0.313244
 2017-01-06  0.662555   0.662555
 2017-01-07  0.586022   0.586022
 2017-01-08  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864
 2017-01-10  0.108871   0.108871

julia> ts = TSFrame([random(10) random(10)], dates, colnames=[:A, :B]) # 列はAとBと名付けられます
(10 x 2) TSFrame with Date Index

 Index       A          B         
 Date        Float64    Float64   
──────────────────────────────────
 2017-01-01  0.768448   0.768448
 2017-01-02  0.940515   0.940515
 2017-01-03  0.673959   0.673959
 2017-01-04  0.395453   0.395453
 2017-01-05  0.313244   0.313244
 2017-01-06  0.662555   0.662555
 2017-01-07  0.586022   0.586022
 2017-01-08  0.0521332  0.0521332
 2017-01-09  0.26864    0.26864
 2017-01-10  0.108871   0.108871

julia> ts = TSFrame(Int64; n=5) # 空のTSFrameで、5列の型はAnyで、Int64インデックス型
0×5 TSFrame with Int64 Index

julia> ts = TSFrame(Date, [(Int64, :col1), (String, :col2), (Float64, :col3)]) # 特定の列名と型を持つ空のTSFrame
0×3 TSFrame with Date Index

julia> ts = TSFrame(Date, [(Int64, "col1"), (String, "col2"), (Float64, "col3")]) # シンボルの代わりに文字列を使用
0×3 TSFrame with Date Index

```
