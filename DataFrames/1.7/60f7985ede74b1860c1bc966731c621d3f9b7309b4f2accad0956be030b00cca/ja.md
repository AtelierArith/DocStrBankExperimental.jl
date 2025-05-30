```
unstack(df::AbstractDataFrame, rowkeys, colkey, value;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
unstack(df::AbstractDataFrame, colkey, value;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
unstack(df::AbstractDataFrame;
        renamecols::Function=identity, allowmissing::Bool=false,
        combine=only, fill=missing, threads::Bool=true)
```

データフレーム `df` をアンスタックします。すなわち、長い形式から広い形式に変換します。

行キーと列キーは、最初に出現した順に並べられます。

# 位置引数

  * `df` : アンスタックされる AbstractDataFrame
  * `rowkeys` : 各行のユニークキーを持つ列。指定しない場合は、`colkey` または `value` でないものをグループ化してキーを見つけます。任意の列セレクタ（`Symbol`、文字列または整数； `:`, `Cols`, `All`, `Between`, `Not`、正規表現、または `Symbol`、文字列または整数のベクター）を使用できます。`rowkeys` に列が含まれていない場合、すべての行は同じキーを持つと見なされます。
  * `colkey` : 幅広い形式で列名を保持する列（`Symbol`、文字列または整数）、デフォルトは `:variable`
  * `values` : 値を格納する列（`Symbol`、文字列または整数）、デフォルトは `:value`

# キーワード引数

  * `renamecols`: `colkey` の各ユニーク値に対して呼び出される関数；作成される列の名前を返す必要があります（通常は文字列または `Symbol` として）。`Symbol` に変換したときに重複する名前は許可されません。デフォルトでは変換は行われません。
  * `allowmissing`: `false`（デフォルト）の場合、`colkey` に `missing` 値が含まれているとエラーが発生します；`true` の場合、`missing` 値を参照する列が作成されます。
  * `combine`: `only`（デフォルト）の場合、`rowkeys` と `colkey` の組み合わせに重複エントリが含まれているとエラーが発生します。そうでない場合、渡された値は、データ内の `rowkeys` と `colkey` の各組み合わせに対してすべての要素を含むベクタービューに対して呼び出される関数でなければなりません。
  * `fill`: 欠損行/列の組み合わせはこの値で埋められます。デフォルトは `missing` です。`value` 列が `CategoricalVector` であり、`fill` が `missing` でない場合、アンスタックされた値列も `CategoricalVector` を保持するために、`fill` は `CategoricalValue` として渡す必要があります。
  * `threads`: `combine` 関数が並行して実行できる別のタスクで実行されるかどうか（同時に複数のグループに適用される可能性があります）。タスクが実際に生成されるかどうかとその数は自動的に決定されます。`combine` が直列実行を必要とする場合やスレッドセーフでない場合は `false` に設定します。

メタデータ：テーブルレベルの `:note` スタイルのメタデータと、行キー列の列レベルの `:note` スタイルのメタデータが保持されます。

# 非推奨

  * `allowduplicates` キーワード引数は非推奨です；代わりに `combine` キーワード引数を使用してください；`allowduplicates=true` に相当するのは `combine=last` で、`allowduplicates=false` に相当するのは `combine=only`（デフォルト）です；

# 例

```jldoctest
julia> wide = DataFrame(id=1:6,
                        a=repeat(1:3, inner=2),
                        b=repeat(1.0:2.0, inner=3),
                        c=repeat(1.0:1.0, inner=6),
                        d=repeat(1.0:3.0, inner=2))
6×5 DataFrame
 Row │ id     a      b        c        d
     │ Int64  Int64  Float64  Float64  Float64
─────┼─────────────────────────────────────────
   1 │     1      1      1.0      1.0      1.0
   2 │     2      1      1.0      1.0      1.0
   3 │     3      2      1.0      1.0      2.0
   4 │     4      2      2.0      1.0      2.0
   5 │     5      3      2.0      1.0      3.0
   6 │     6      3      2.0      1.0      3.0

julia> long = stack(wide)
18×4 DataFrame
 Row │ id     a      variable  value
     │ Int64  Int64  String    Float64
─────┼─────────────────────────────────
   1 │     1      1  b             1.0
   2 │     2      1  b             1.0
   3 │     3      2  b             1.0
   4 │     4      2  b             2.0
   5 │     5      3  b             2.0
   6 │     6      3  b             2.0
   7 │     1      1  c             1.0
   8 │     2      1  c             1.0
  ⋮  │   ⋮      ⋮       ⋮         ⋮
  12 │     6      3  c             1.0
  13 │     1      1  d             1.0
  14 │     2      1  d             1.0
  15 │     3      2  d             2.0
  16 │     4      2  d             2.0
  17 │     5      3  d             3.0
  18 │     6      3  d             3.0
                         3 rows omitted

julia> unstack(long)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :variable, :value)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :id, :variable, :value)
6×4 DataFrame
 Row │ id     b         c         d
     │ Int64  Float64?  Float64?  Float64?
─────┼─────────────────────────────────────
   1 │     1       1.0       1.0       1.0
   2 │     2       1.0       1.0       1.0
   3 │     3       1.0       1.0       2.0
   4 │     4       2.0       1.0       2.0
   5 │     5       2.0       1.0       3.0
   6 │     6       2.0       1.0       3.0

julia> unstack(long, [:id, :a], :variable, :value)
6×5 DataFrame
 Row │ id     a      b         c         d
     │ Int64  Int64  Float64?  Float64?  Float64?
─────┼────────────────────────────────────────────
   1 │     1      1       1.0       1.0       1.0
   2 │     2      1       1.0       1.0       1.0
   3 │     3      2       1.0       1.0       2.0
   4 │     4      2       2.0       1.0       2.0
   5 │     5      3       2.0       1.0       3.0
   6 │     6      3       2.0       1.0       3.0

julia> unstack(long, :id, :variable, :value, renamecols=x->Symbol(:_, x))
6×4 DataFrame
 Row │ id     _b        _c        _d
     │ Int64  Float64?  Float64?  Float64?
─────┼─────────────────────────────────────
   1 │     1       1.0       1.0       1.0
   2 │     2       1.0       1.0       1.0
   3 │     3       1.0       1.0       2.0
   4 │     4       2.0       1.0       2.0
   5 │     5       2.0       1.0       3.0
   6 │     6       2.0       1.0       3.0
```

上記の拡張された結果にはいくつかの違いがあることに注意してください。

```jldoctest
julia> df = DataFrame(id=["1", "1", "2"],
                      variable=["Var1", "Var2", "Var1"],
                      value=[1, 2, 3])
3×3 DataFrame
 Row │ id      variable  value
     │ String  String    Int64
─────┼─────────────────────────
   1 │ 1       Var1          1
   2 │ 1       Var2          2
   3 │ 2       Var1          3

julia> unstack(df, :variable, :value, fill=0)
2×3 DataFrame
 Row │ id      Var1   Var2
     │ String  Int64  Int64
─────┼──────────────────────
   1 │ 1           1      2
   2 │ 2           3      0

julia> df = DataFrame(cols=["a", "a", "b"], values=[1, 2, 4])
3×2 DataFrame
 Row │ cols    values
     │ String  Int64
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ b            4

julia> unstack(df, :cols, :values, combine=copy)
1×2 DataFrame
 Row │ a        b
     │ Array…?  Array…?
─────┼──────────────────
   1 │ [1, 2]   [4]

julia> unstack(df, :cols, :values, combine=sum)
1×2 DataFrame
 Row │ a       b
     │ Int64?  Int64?
─────┼────────────────
   1 │      3       4
```
