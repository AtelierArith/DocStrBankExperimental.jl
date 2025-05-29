```
pairwise(f, x[, y];
         symmetric::Bool=false, skipmissing::Symbol=:none)
```

`f`をイテレータ`x`と`y`のすべての可能なペアのエントリに適用した結果を保持する行列を返します。行は`x`のエントリに対応し、列は`y`のエントリに対応します。`y`が省略された場合、`x`自身との交差を持つ正方行列が返されます。

特別なケースとして、`f`が`cor`の場合、`x`と`y`のエントリが同一である（`===`に従う）対角セルは、`missing`、`NaN`、または`Inf`のエントリが存在しても1に設定されます。

# キーワード引数

  * `symmetric::Bool=false`: `true`の場合、`f`は行列の下三角のみを計算するために呼び出され、これらの値が上三角を埋めるためにコピーされます。`y`が省略された場合のみ許可されます。`f`が`cor`または`cov`の場合はデフォルトで`true`になります。
  * `skipmissing::Symbol=:none`: `:none`（デフォルト）の場合、入力の欠損値は修正なしで`f`に渡されます。`:pairwise`を使用すると、`f`に渡される2つのベクトルのいずれかに`missing`値があるエントリをスキップします。`:listwise`を使用すると、`x`または`y`のいずれかのベクトルに`missing`値があるエントリをスキップします。これは多くのエントリを削除する可能性があります。`x`と`y`のエントリがベクトルである場合のみ許可されます。

# 例

```jldoctest
julia> using StatsBase, Statistics

julia> x = [1 3 7
            2 5 6
            3 8 4
            4 6 2];

julia> pairwise(cor, eachcol(x))
3×3 Matrix{Float64}:
  1.0        0.744208  -0.989778
  0.744208   1.0       -0.68605
 -0.989778  -0.68605    1.0

julia> y = [1 3 missing
            2 5 6
            3 missing 2
            4 6 2];

julia> pairwise(cor, eachcol(y), skipmissing=:pairwise)
3×3 Matrix{Float64}:
  1.0        0.928571  -0.866025
  0.928571   1.0       -1.0
 -0.866025  -1.0        1.0
```
