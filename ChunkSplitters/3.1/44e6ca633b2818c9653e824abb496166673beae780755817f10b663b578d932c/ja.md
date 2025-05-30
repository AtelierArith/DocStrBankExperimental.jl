```
index_chunks(collection;
    n::Union{Nothing, Integer}=nothing,
    size::Union{Nothing, Integer}=nothing,
    [split::Split=Consecutive(),]
    [minsize::Union{Nothing,Integer}=nothing,]
)

`collection`の*インデックス*を`n`個のチャンクに分割するイテレータを返します（`n`が指定されている場合）または特定のサイズのチャンクに分割します（`size`が指定されている場合）。返されたイテレータは、`collection`の*インデックス*のチャンクを1つずつ処理するために使用できます。`collection`の*要素*のチャンクを処理したい場合は、代わりに`chunks(...)`を確認してください。

キーワード引数`n`と`size`は相互に排他的です。

### キーワード引数（オプション）

  * `split`は分割戦略、すなわちチャンク間のインデックスの分配を決定するために使用できます。`split = Consecutive()`（デフォルト）の場合、チャンクは連続したインデックスを保持し、可能な限り同じ数のインデックスを保持します。`split = RoundRobin()`の場合、インデックスはラウンドロビン方式でチャンクに割り当てられます。
  * `minsize`はチャンクの最小サイズを指定するために使用でき、`n`キーワードと組み合わせて使用できます。指定された`n`に対して、チャンクが`minsize`より小さい場合、各チャンクが少なくとも`minsize`の長さになるようにチャンクの数が減少します。デフォルトでは、キーワードが`nothing`に設定されているとき、`minsize == 1`です。`minsize`がコレクションの長さより大きい場合、チャンクは1つだけになります。

### 注目すべき点

実行中のチャンクインデックスが必要な場合は、`chunks`と`enumerate`を組み合わせることができます。特に、`enumerate(index_chunks(...))`は`@threads`と組み合わせて使用できます。

### 要件

入力`collection`の型は、`firstindex`、`lastindex`、および`length`関数が定義されている必要があり、さらに`ChunkSplitters.is_chunkable(::typeof(collection)) = true`である必要があります。標準で、`AbstractArray`と`Tuple`がサポートされています。

## 例

```

jldoctest julia> using ChunkSplitters

julia> x = rand(7);

julia> collect(index_chunks(x; n=3)) 3-element Vector{UnitRange{Int64}}:  1:3  4:5  6:7

julia> collect(enumerate(index_chunks(x; n=3))) 3-element Vector{Tuple{Int64, UnitRange{Int64}}}:  (1, 1:3)  (2, 4:5)  (3, 6:7)

julia> collect(index_chunks(1:7; size=3)) 3-element Vector{UnitRange{Int64}}:  1:3  4:6  7:7 ```
