```
@eachrow!(df, body)
```

データフレームの各行に対してインプレースで操作を行います。これは次のように似ています。

```
for row in eachrow(df)
    ... # `df`を変更するアクション。
end
```

制御フローと `begin end` ブロックをサポートしています。`@eachrow! df` によって誘発される「環境」は暗黙的に `df` の単一行であるため、`@with` のように要素ごとの対応物ではなく、通常の演算子と比較を使用してください。`@eachrow!` 内のスコープはハードスコープです。

`eachrow!` は新しい列を割り当てるための特別な構文もサポートしています。構文 `@newcol x::Vector{Int}` は、`Int` のエルタイプを持つ `Vector` コンテナを持つ新しい未初期化の列 `:x` を割り当てます。この機能により、データ変換のために `eachrow` を使用するのが容易になります。`_N` はデータフレームの行数を表し、`_DF` は追加された列を含む `dataframe` を表し、`row` は現在の行のインデックスを表します。

行への変更は `df` に直接影響します。この操作はデータフレームをインプレースで変更します。同じ構文を使用しますが、新しいデータフレームを割り当てる [`@eachrow`](@ref) を参照してください。

`@transform!` と同様に、`@eachrow!` は変数として保存された列名を操作するために `$` を使用することをサポートしています。`Symbol` の `Vector` のような複数列セレクタと `$` を使用することは現在サポートされていません。

`@eachrow!` は `for` ループの薄いラッパーです。その結果、`@eachrow!` ブロック内では、予約語引数 `break` と `continue` は `for` ループで書かれた場合と同じように機能します。`break` と `continue` に影響されない行は変更されませんが、変更された行にはまだ存在します。また、`@eachrow!` が `for` ループであるため、`@eachrow` ブロック内でグローバル変数を再割り当てすることは推奨されません。

### 引数

  * `df` : `AbstractDataFrame`
  * `expr` : 行ごとに操作される式

### 戻り値

変更された `AbstractDataFrame`。

### 例

```julia
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> let x = 0
            @eachrow! df begin
                if :A + :B == 3
                    x += 1
                end
            end  #  let がないとこれは動作しません
            x
        end
2

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           if :A > :B
               :A = 0
           end
       end;

julia> df2
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      2
   2 │     0      1
   3 │     0      2

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           @newcol :colX::Vector{Float64}
           :colX = :B == 2 ? pi * :A : :B
       end
3×3 DataFrame
 Row │ A      B      colX
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  3.14159
   2 │     2      1  1.0
   3 │     3      2  9.42478

julia> varA = :A; varB = :B;

julia> df2 = copy(df);

julia> @eachrow! df2 begin
           @newcol :colX::Vector{Float64}
           :colX = $varB == 2 ? pi * $varA : $varB
       end
3×3 DataFrame
 Row │ A      B      colX
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  3.14159
   2 │     2      1  1.0
   3 │     3      2  9.42478

julia> x = [1, 1, 1];

julia> @eachrow! df begin
           x[row] = :A
       end;

julia> x
3-element Vector{Int64}:
 1
 2
 3

julia> @eachrow! df begin
           @newcol :m::Vector{Float64}
           :m = mean(_DF[:, row])
       end
3×3 DataFrame
 Row │ A      B      m
     │ Int64  Int64  Float64
─────┼───────────────────────
   1 │     1      2  2.0
   2 │     2      1  1.66667
   3 │     3      2  1.22222

julia> @eachrow! df begin
           :A == 2 && continue
           println(:A)
       end;
1
3
```
