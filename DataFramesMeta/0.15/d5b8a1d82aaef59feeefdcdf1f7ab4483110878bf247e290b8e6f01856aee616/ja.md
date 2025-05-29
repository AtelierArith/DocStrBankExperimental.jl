```
@eachrow(df, body)
```

データフレームの各行に対して操作を行い、新しいデータフレームを生成します。これは次のように似ています。

```
for row in eachrow(copy(df))
    ...
end
```

制御フローと `begin end` ブロックをサポートしています。`@eachrow df` によって誘導される「環境」は暗黙的に `df` の単一行であるため、`@with` のように要素ごとの対応物の代わりに通常の演算子と比較を使用してください。`@eachrow` 内のスコープはハードスコープです。

`eachrow` は新しい列を割り当てるための特別な構文もサポートしています。構文 `@newcol x::Vector{Int}` は、`Int` のエレメンタイプを持つ `Vector` コンテナを持つ新しい未初期化の列 `:x` を割り当てます。この機能により、データ変換のために `eachrow` を使用することが容易になります。`_N` はデータフレームの行数を表すために導入され、`_DF` は追加された列を含む `DataFrame` を表し、`row` は現在の行のインデックスを表します。

行への変更は `df` に影響を与えず、代わりに `@eachrow` によって新しく割り当てられたデータフレームが返されます。また、返されたデータフレームは `df` と列を共有しません。データフレームをインプレースで修正する同じ構文を使用する [`@eachrow!`](@ref) を参照してください。

`@transform` と同様に、`@eachrow` は変数として保存された列名を操作するために `$` の使用をサポートしています。`Symbol` の `Vector` のような複数列セレクタと `$` を使用することは現在サポートされていません。

`@eachrow` は `for` ループの薄いラッパーです。その結果、`@eachrow` ブロック内では、予約語引数 `break` と `continue` は `for` ループで書かれた場合と同じように機能します。`break` と `continue` に影響を受けない行は変更されず、返されたデータフレームにも存在します。また、`@eachrow` が `for` ループであるため、`@eachrow` ブロック内でグローバル変数を再代入することは推奨されません。

### 引数

  * `df` : `AbstractDataFrame`
  * `expr` : 行ごとに操作される式

### 返り値

修正された `AbstractDataFrame`。

### 例

```julia
julia> using DataFramesMeta

julia> df = DataFrame(A = 1:3, B = [2, 1, 2]);

julia> let x = 0
            @eachrow df begin
                if :A + :B == 3
                    x += 1
                end
            end  #  let がないとこれは動作しません
            x
        end
2

julia> @eachrow df begin
            if :A > :B
                :A = 0
            end
        end
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      2
   2 │     0      1
   3 │     0      2

julia> df2 = @eachrow df begin
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

julia> df2 = @eachrow df begin
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

julia> @eachrow df begin
           x[row] = :A
       end;

julia> x
3-element Vector{Int64}:
 1
 2
 3

julia> @eachrow df begin
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

julia> @eachrow df begin
           :A == 2 && continue
           println(:A)
       end;
1
3

```
