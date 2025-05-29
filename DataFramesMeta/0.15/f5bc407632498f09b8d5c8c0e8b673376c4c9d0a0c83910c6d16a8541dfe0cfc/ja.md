```
@with(d, expr)
```

`@with` は DataFrame の列キーをシンボルとして参照できるようにします。

### 引数

  * `d` : AbstractDataFrame 型
  * `expr` : `d` で評価する式

### 詳細

`@with` は、シンボル（例: `:colA`）で示されたすべての列を式本体から解析することによって機能します。次に、式本体をラップし、列を関数引数として渡す関数が作成されます。この関数が呼び出されます。操作は効率的です。なぜなら：

  * 擬似匿名関数が定義されるため、型が安定しています。
  * 列は参照として渡されるため、DataFrame のインデックス付けが不要です。

次のようになります。

```julia
@with(d, :a .+ :b .+ 1)
```

これは次のようになります。

```julia
tempfun(a, b) = a .+ b .+ 1
tempfun(d[!, :a], d[!, :b])
```

式が `^(expr)` でラップされている場合、`expr` はそのまま渡されます。式が `$(expr)` でラップされている場合、列はシンボルではなく変数 `expr` で参照されます。

`@with` に提供された式が `@byrow` で始まる場合、`@with` ブロックによって作成された関数はデータフレームの列に沿ってブロードキャストされます。

### 例

```jldoctest
julia> using DataFramesMeta

julia> y = 3;

julia> df = DataFrame(x = 1:3, y = [2, 1, 2]);

julia> x = [2, 1, 0];

julia> @with(df, :y .+ 1)
3-element Vector{Int64}:
 3
 2
 3

julia> @with(df, :x + x)
3-element Vector{Int64}:
 3
 3
 3

julia> @with df begin
            res = 0.0
            for i in 1:length(:x)
                res += :x[i] * :y[i]
            end
            res
        end
10.0

julia> @with(df, df[:x .> 1, ^(:y)]) # ^ は :y をそのままにすることを意味します
2-element Vector{Int64}:
 1
 2

julia> colref = :x;

julia> @with(df, :y + $colref) # df[!, :y] + df[!, colref] と同等
3-element Vector{Int64}:
 3
 3
 5

julia> @with df @byrow :x * :y
3-element Vector{Int64}:
 2
 2
 6

```

!!! 注     `@with` は関数を作成するため、`@with` 内のスコープはローカルスコープです。親の変数は読み取ることができます。親スコープの変数への書き込みは、親のスコープのタイプによって異なります。親スコープがグローバルスコープである場合、`global` キーワードを使用せずに変数に代入することはできません。親スコープがローカルスコープ（関数や let ブロックの内部など）の場合、親スコープに代入するために `global` キーワードは必要ありません。

!!! 注     現在、`@with` ブロック内で `AsTable` を使用することはサポートされていません。
