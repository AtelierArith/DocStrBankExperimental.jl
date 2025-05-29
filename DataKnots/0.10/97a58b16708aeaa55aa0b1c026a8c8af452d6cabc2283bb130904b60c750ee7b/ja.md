```
DataKnot(Pair{Symbol}...)
```

このコンストラクタは、データセットに名前をバインドし、クエリを開始するために使用できるようにします。作成されたノットは、各自の値を持つ単一のトップレベルレコードを持っています。

```jldoctest
julia> test_knot = DataKnot(:dataset=>'a':'c')
│ dataset │
┼─────────┼
│ a; b; c │

julia> test_knot[It.dataset]
  │ dataset │
──┼─────────┼
1 │ a       │
2 │ b       │
3 │ c       │
```

このコンストラクタへの引数は `convert` を通じて実行されます。

---

```
convert(DataKnot, val)
```

このコンバータは、与えられた値をラップして、クエリを開始するために使用できるようにします。

空のノットは `missing` を使って構築できます。

```jldoctest
julia> convert(DataKnot, missing)
(empty)
```

複数のノットはベクトルから構築されます。

```jldoctest
julia> convert(DataKnot, 'a':'c')
──┼───┼
1 │ a │
2 │ b │
3 │ c │
```

`CSV` ファイルのように `Table` インターフェースに準拠したオブジェクトは、DataKnot に変換できます。

```jldoctest
julia> using CSV;

julia> csv_file = "k,v\na,1\nb,\n" |> IOBuffer |> CSV.File;

julia> convert(DataKnot, csv_file)
  │ k  v │
──┼──────┼
1 │ a  1 │
2 │ b    │
```

---

```
get(::DataKnot)
```

`get` を使用して、ノットが保持している基礎となる値を抽出します。

```jldoctest
julia> get(convert(DataKnot, "Hello World"))
"Hello World"
```

---

```
getindex(::DataKnot, X; kwargs...)
```

配列インデックス表記を使用してノットをクエリできます。

```jldoctest
julia> convert(DataKnot, (dataset='a':'c',))[Count(It.dataset)]
┼───┼
│ 3 │
```

クエリパラメータはキーワード引数として提供されます。

```jldoctest
julia> convert(DataKnot, 1:3)[PWR=2, It .^ It.PWR]
──┼───┼
1 │ 1 │
2 │ 4 │
3 │ 9 │
```
