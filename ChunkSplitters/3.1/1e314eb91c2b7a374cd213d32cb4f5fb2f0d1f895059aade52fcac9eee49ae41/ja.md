```
chunks(collection;
    n::Union{Nothing, Integer}=nothing,
    size::Union{Nothing, Integer}=nothing,
    [split::Split=Consecutive(),]
    [minsize::Union{Nothing,Integer}=nothing,]
)
```

`collection`の*要素*を`n`個のチャンクに分割するイテレータを返します（`n`が指定されている場合）または特定のサイズのチャンクに分割します（`size`が指定されている場合）。コピーを避けるために、チャンクは一般的に元のコレクションへのビューを保持します。返されたイテレータは、`collection`の*要素*のチャンクを1つずつ処理するために使用できます。`collection`の*インデックス*のチャンクを処理したい場合は、代わりに`index_chunks(...)`を確認してください。

キーワード引数`n`と`size`は相互に排他的です。

### キーワード引数（オプション）

  * `split`は分割戦略、すなわちチャンク間のインデックスの分配を決定するために使用できます。`split = Consecutive()`（デフォルト）の場合、チャンクは連続した要素を保持し、可能な限り同じ数の要素を保持します。`split = RoundRobin()`の場合、要素はラウンドロビン方式でチャンクに割り当てられます。
  * `minsize`はチャンクの最小サイズを指定するために使用でき、`n`キーワードと組み合わせて使用できます。指定された`n`に対して、チャンクが`minsize`より小さい場合、各チャンクが少なくとも`minsize`の長さになるようにチャンクの数が減少します。デフォルトでは、キーワードが`nothing`に設定されている場合、`minsize == 1`です。`minsize`がコレクションの長さより大きい場合、チャンクは1つだけになります。

### 注目すべき点

実行中のチャンクインデックスが必要な場合は、`chunks`を`enumerate`と組み合わせることができます。特に、`enumerate(chunks(...))`は`@threads`と組み合わせて使用できます。

### 要件

`index_chunks`の要件に加えて（ドキュメントを参照）、入力`collection`の型は`view`の実装を持っている必要があります。特に、`view(::typeof(collection), ::UnitRange)`および`view(::typeof(collection), ::StepRange)`です。標準で、`AbstractArray`と`Tuple`がサポートされています。

## 例

```jldoctest
julia> using ChunkSplitters

julia> x = [1.2, 3.4, 5.6, 7.8, 9.0];

julia> collect(chunks(x; n=3))
3-element Vector{SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}}:
 [1.2, 3.4]
 [5.6, 7.8]
 [9.0]

julia> collect(enumerate(chunks(x; n=3)))
3-element Vector{Tuple{Int64, SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}}}:
 (1, [1.2, 3.4])
 (2, [5.6, 7.8])
 (3, [9.0])

julia> collect(chunks(x; size=3))
2-element Vector{SubArray{Float64, 1, Vector{Float64}, Tuple{UnitRange{Int64}}, true}}:
 [1.2, 3.4, 5.6]
 [7.8, 9.0]
```
