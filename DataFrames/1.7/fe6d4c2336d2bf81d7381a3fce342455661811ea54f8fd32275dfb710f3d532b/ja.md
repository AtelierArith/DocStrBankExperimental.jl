```
combine(df::AbstractDataFrame, args...;
        renamecols::Bool=true, threads::Bool=true)
combine(f::Callable, df::AbstractDataFrame;
        renamecols::Bool=true, threads::Bool=true)
combine(gd::GroupedDataFrame, args...;
        keepkeys::Bool=true, ungroup::Bool=true,
        renamecols::Bool=true, threads::Bool=true)
combine(f::Base.Callable, gd::GroupedDataFrame;
        keepkeys::Bool=true, ungroup::Bool=true,
        renamecols::Bool=true, threads::Bool=true)

新しいデータフレームを作成し、`df`または`gd`から`args`で指定された列を含めて返します。結果は、渡された変換によって返される値によって決定される任意の数の行を持つことができます。

以下に、DataFrames.jlによってサポートされるすべての変換関数の一般的なルールが詳しく説明され、比較されています。

これらの操作は、`AbstractDataFrame`（分割と結合のステップをスキップした場合）と`GroupedDataFrame`の両方でサポートされています。技術的には、`AbstractDataFrame`は、列がない状態でグループ化されていると見なされます（つまり、単一のグループを持つか、空の場合はゼロのグループを持つことを意味します）。この場合の唯一の違いは、`keepkeys`および`ungroup`キーワード引数（以下に説明）がサポートされず、データフレームが常に返されることです。この場合、分割と結合のステップは存在しません。

グループごとに操作を実行するには、まず`groupby`関数を使用してデータフレームから`GroupedDataFrame`オブジェクトを作成する必要があります。この関数は2つの引数を取ります：（1）グループ化されるデータフレーム、（2）グループ化する列のセットです。

その後、次の関数のいずれかを使用して各グループに操作を適用できます：

  * `combine`: 各グループごとに返される行数に制限を設けず、返された値は`GroupedDataFrame`内のグループの順序に従って縦に連結されます。通常、グループごとの要約統計を計算するために使用されます。`GroupedDataFrame`の場合、グループ化された列が保持されている場合、それらは結果の最初の列として配置されます。
  * `select`: ソースデータフレームと同じ行数と順序を持つデータフレームを返し、新しく計算された列のみを含みます。`select!`は`select`のインプレースバージョンです。`GroupedDataFrame`の場合、グループ化された列が保持されている場合、それらは結果の最初の列として配置されます。
  * `transform`: ソースデータフレームと同じ行数と順序を持つデータフレームを返し、ソースからのすべての列と新しく計算された列を含みます。`transform!`は`transform`のインプレースバージョンです。ソースデータフレームの既存の列は結果の最初の列として配置されます。

特別なケースとして、ゼログループの`GroupedDataFrame`が渡された場合、操作の結果は、0行の引数を渡して変換関数を1回呼び出すことによって決定されます。この操作の出力は、生成された列の数と型を特定するためだけに使用されますが、結果はゼロ行です。

これらのすべての関数は、`DataFrame`の各サブセットに適用する1つ以上の関数の仕様を受け取ります。この仕様は次の形式のいずれかです：

1. 標準の列セレクタ（整数、`Symbol`、文字列、整数のベクトル、`Symbol`のベクトル、文字列のベクトル、`All`、`Cols`、`:`、`Between`、`Not`および正規表現）
2. `cols => function`ペアは、`function`が列`cols`を持つ位置引数で呼び出されることを示します。ここで、`cols`は有効な列セレクタである必要があります。この場合、ターゲット列名は自動的に生成され、`function`が単一の値またはベクトルを返すと仮定されます。生成された名前は、デフォルトでソース列名と`function`名を連結することによって作成されます（以下の例を参照）。
3. `cols => function => target_cols`形式は、ターゲット列または列を明示的に指定します。これは単一の名前（`Symbol`または文字列）、名前のベクトル、または`AsTable`でなければなりません。さらに、`cols`で選択された列の名前を含む文字列または文字列のベクトルを引数として受け取り、ターゲット列名を返す`Function`であることもできます（`AsTable`以外のすべての受け入れられる型が許可されます）。
4. `col => target_cols`ペアは、列`col`を`target_cols`にリネームします。`target_cols`は単一の名前（`Symbol`または文字列）、名前のベクトル、または`AsTable`でなければなりません。
5. 列に依存しない操作`function => target_cols`または特定の`function`のための単に`function`は、入力列が省略されます。`target_cols`がない場合、新しい列は`function`と同じ名前になります。そうでない場合、単一の名前（`Symbol`または文字列）でなければなりません。サポートされている`function`は：

      * `nrow`は、各グループの行数を効率的に計算します。
      * `proprow`は、各グループの行の割合を効率的に計算します。
      * `eachindex`は、各グループ内の各行の番号を保持するベクトルを返します。
      * `groupindices`は、グループ番号を返します。
6. 変換がポイント2から5で説明された`Pair`構文で指定されたベクトルまたは行列
7. `GroupedDataFrame`が処理されている場合は、各グループに対応する`SubDataFrame`で呼び出される関数、または`AbstractDataFrame`が処理されている場合はデータフレーム自体で呼び出される関数。この形式は、グループの数が少ない場合や非常に多くの列が処理される場合を除いて、パフォーマンスが悪いため避けるべきです（この場合、`SubDataFrame`は過剰なコンパイルを回避します）。

注意！`x => y`の形式の式が渡された場合、特別な便利形式`nrow => target_cols`を除いて、常に`cols => function`として解釈されます。特に、次の式`function => target_cols`は有効な変換仕様ではありません。

注意！`cols`または`target_cols`が`All`、`Cols`、`Between`、または`Not`のいずれかである場合、`.=>`を使用したブロードキャストがサポートされており、`names(df, cols)`または`names(df, target_cols)`の結果をブロードキャストするのと同等です。これは、データフレームスコープ内で選択された列名に置き換えた後にブロードキャストが発生したかのように動作します。

すべての関数には2つのタイプのシグネチャがあります。1つは、最初の引数として`GroupedDataFrame`を取り、次の引数として上記で説明された任意の数の変換を取ります。2つ目のタイプのシグネチャは、最初の引数として`Function`または`Type`を渡し、2番目の引数として`GroupedDataFrame`を渡すものです（`map`に似ています）。

特別なルールとして、`cols => function`および`cols => function => target_cols`構文では、`cols`が`AsTable`オブジェクトでラップされている場合、`function`に`cols`で選択された列を含む`NamedTuple`が渡されます。[`DataFrames.table_transformation`](@ref)のドキュメントは、この機能に関する詳細情報を提供し、特にパフォーマンスの考慮事項をカバーしています。

`function`が返すことが許可されているものは、`target_cols`の値によって決まります：

1. `cols`と`target_cols`の両方が省略されている場合（つまり、`function`のみが渡されている場合）、データフレーム、行列、`NamedTuple`、`Tables.AbstractRow`、または`DataFrameRow`を返すと、結果に複数の列が生成されます。他の値を返すと、単一の列が生成されます。
2. `target_cols`が`Symbol`または文字列の場合、関数は単一の列を返すと見なされます。この場合、データフレーム、行列、`NamedTuple`、`Tables.AbstractRow`、または`DataFrameRow`を返すとエラーが発生します。
3. `target_cols`が`Symbol`または文字列のベクトルまたは`AsTable`の場合、`function`は複数の列を返すと見なされます。`function`が`AbstractDataFrame`、`NamedTuple`、`DataFrameRow`、`Tables.AbstractRow`、`AbstractMatrix`のいずれかを返す場合、上記のポイント1で説明されたルールが適用されます。`function`が`AbstractVector`を返す場合、このベクトルの各要素は`keys`関数をサポートする必要があり、`keys`は`Symbol`、文字列、または整数のコレクションを返す必要があります。`keys`の返り値はすべての要素で同一でなければなりません。次に、`keys`関数の返り値の要素数に応じて、生成される列の数が決まります。`target_cols`が`AsTable`の場合、名前はキー名と等しく設定されますが、`keys`が整数を返す場合は、`x`で接頭辞が付けられます（したがって、列名は`x1`、`x2`などになります）。`target_cols`が`Symbol`または文字列のベクトルの場合、上記のルールで生成された列名は無視され、`target_cols`で置き換えられます（この場合、列の数は`target_cols`の長さと同じでなければなりません）。`fun`が他の型の値を返す場合、それはTables.jl APIに準拠したテーブルであると見なされ、`Tables.columntable`関数が呼び出されて結果の列とその名前が取得されます。名前は、`target_cols`が`AsTable`の場合は保持され、`target_cols`が`Symbol`または文字列のベクトルの場合は置き換えられます。

これらのすべてのケースにおいて、`function`は単一の行または複数の行を返すことができます。特別なルールとして、`Ref`または0次元の`AbstractArray`でラップされた値はアンラップされ、単一の行として扱われます。

`select`/`select!`および`transform`/`transform!`は常に、ソースと同じ行数と順序を持つデータフレームを返します（`GroupedDataFrame`がそのグループを再配置しても）。ただし、選択の結果、結果のデータフレームにゼロ列がある場合（この場合、結果はゼロ行になります）。

`combine`の場合、返されたオブジェクトの行は`GroupedDataFrame`内のグループの順序で表示されます。関数は各グループに対して任意の数の行を返すことができますが、返されるオブジェクトの種類と列の数および名前は、すべてのグループで同じでなければなりません。ただし、`DataFrame()`または`NamedTuple()`が返される場合は、特定のグループがスキップされます。

複数の変換が要求される場合、単一の値とベクトルを混在させることが許可されています。この場合、単一の値は返されたベクトルで指定された列の長さに一致するように繰り返されます。

`function`を全体の列ではなく各行に適用するには、`ByRow`構造体でラップできます。`cols`は任意の列インデックス構文を使用でき、この場合、`function`は`cols`で指定された各列の引数を1つ受け取るか、`AsTable`で指定された場合はそれらの`NamedTuple`を受け取ります。`ByRow`が使用される場合、`cols`が空の列のセットを選択することが許可され、この場合、`function`は引数なしで各行に対して呼び出され、空の`NamedTuple`が渡されます。

列名のコレクションが渡された場合、ターゲットデータフレームでの重複列名の要求が許可されます（例：`select!(df, [:a], :, r"a")`が許可されます）し、最初の出現のみが使用されます。特に、列`:col`をデータフレームの最初の位置に移動するための構文は`select!(df, :col, :)`です。逆に、リネーム、変換、および単一列選択操作の出力列名は一意でなければならないため、例えば`select!(df, :a, :a => :a)`や`select!(df, :a, :a => ByRow(sin) => :a)`は許可されません。

一般に、変換によって返される列は、ターゲットデータフレームにコピーなしで保存されます。このルールの例外は、ソースデータフレームの列がターゲットデータフレームで再利用される場合です。これは、`:x1`、`[:x1, :x2]`、`:x1 => :x2`、`:x1 => identity => :x2`、または`:x1 => (x -> @view x[inds])`のような式を介して発生する可能性があります（最後のケースでは、ソース列は間接的にビューを介して再利用されます）。このような場合の動作は、`copycols`キーワード引数の値によって異なります：

  * `copycols=true`の場合、そのような変換の結果は常にソース列またはそのビューのコピーを実行します。
  * `copycols=false`の場合、ターゲットデータフレームに同じ列を複数回保存しないようにコピーが実行されます。より正確には、列が最初に使用されるときはコピーは行われませんが、ソース列のその後の再利用（`===`を使用して比較される場合、ソース列のビューは除外されます）はコピーを実行します。

`transform!`または`select!`を実行する場合、`copycols=false`であることを前提としています。

`df`が`SubDataFrame`であり、`copycols=true`の場合、`DataFrame`が返され、同じコピーのルールが`DataFrame`入力に適用されます。これは特に、選択された列がコピーされることを意味します。`copycols=false`の場合、列をコピーせずに`SubDataFrame`が返され、この場合、列の変換またはリネームは許可されません。

`GroupedDataFrame`が渡され、`threads=true`（デフォルト）である場合、指定された各変換のために別のタスクが生成されます。各変換は、Juliaスレッドの数だけタスクを生成し、グループの処理をそれらに分割します（ただし、現在、`sum`のような最適化された実装を持つ変換や、複数の行を返す変換は、すべてのグループに対して単一のタスクを使用します）。これにより、Juliaが複数のスレッドで起動された場合に並列操作が可能になります。したがって、渡された変換関数はグローバル変数を変更してはならず（つまり、純粋でなければなりません）、並列アクセスを制御するためにロックを使用するか、`threads=false`を渡してマルチスレッドを無効にする必要があります。将来的には、並列処理が他のケースにも拡張される可能性があるため、この要件は`DataFrame`入力にも適用されます。

操作のパフォーマンスを向上させるために、一部の変換は最適化された実装を呼び出します。詳細については、[`DataFrames.table_transformation`](@ref)を参照してください。

# キーワード引数

  * `renamecols::Bool=true` : `cols => function`形式で自動生成された列名に変換関数の名前を含めるかどうか。
  * `keepkeys::Bool=true` : `gd`のグループ化列を返されるデータフレームに保持するかどうか。
  * `ungroup::Bool=true` : `gd`の操作の返り値がデータフレームであるべきか、`GroupedDataFrame`であるべきか。
  * `threads::Bool=true` : 変換が並列で実行できる別のタスクで実行されるかどうか（同時に複数の行またはグループに適用される可能性があります）。タスクが実際に生成されるかどうか、またその数は自動的に決定されます。いくつかの変換が直列実行を必要とする場合やスレッドセーフでない場合は、`false`に設定してください。

メタデータ：この関数は、テーブルレベルの`:note`スタイルのメタデータを伝播します。列レベルの`:note`スタイルのメタデータは、次の条件を満たす場合に伝播されます：a) 単一の列が単一の列に変換され、列の名前が変更されない場合（これにはすべての列選択操作が含まれます）、または b) 単一の列が`identity`または`copy`で単一の列に変換される場合、列名が変更されても（これには列のリネームが含まれます）。特別なケースとして、`GroupedDataFrame`の場合、出力がグループ化列と同じ名前を持ち、`keepkeys=true`の場合、メタデータは元のグループ化列から取得されます。

# 例

```

jldoctest julia> df = DataFrame(a=1:3, b=4:6) 3×2 DataFrame  Row │ a      b      │ Int64  Int64 ─────┼──────────────    1 │     1      4    2 │     2      5    3 │     3      6

julia> combine(df, :a => sum, nrow, renamecols=false) 1×2 DataFrame  Row │ a      nrow      │ Int64  Int64 ─────┼──────────────    1 │     6      3

julia> combine(df, :a => ByRow(sin) => :c, :b) 3×2 DataFrame  Row │ c         b      │ Float64   Int64 ─────┼─────────────────    1 │ 0.841471      4    2 │ 0.909297      5    3 │ 0.14112       6

julia> combine(df, :, [:a, :b] => (a, b) -> a .+ b .- sum(b)/length(b)) 3×3 DataFrame  Row │ a      b      a*b*function      │ Int64  Int64  Float64 ─────┼────────────────────────────    1 │     1      4           0.0    2 │     2      5           2.0    3 │     3      6           4.0

julia> combine(df, All() .=> [minimum maximum]) 1×4 DataFrame  Row │ a*minimum  b*minimum  a*maximum  b*maximum      │ Int64      Int64      Int64      Int64 ─────┼────────────────────────────────────────────    1 │         1          4          3          6

julia> using Statistics

julia> combine(df, AsTable(:) => ByRow(mean), renamecols=false) 3×1 DataFrame  Row │ a_b      │ Float64 ─────┼─────────    1 │     2.5    2 │     3.5    3 │     4.5

julia> combine(df, AsTable(:) => ByRow(mean) => x -> join(x, "*")) 3×1 DataFrame  Row │ a*b      │ Float64 ─────┼─────────    1 │     2.5    2 │     3.5    3 │     4.5

julia> combine(first, df) 1×2 DataFrame  Row │ a      b      │ Int64  Int64 ─────┼──────────────    1 │     1      4

julia> df = DataFrame(a=1:3, b=4:6, c=7:9) 3×3 DataFrame  Row │ a      b      c      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     1      4      7    2 │     2      5      8    3 │     3      6      9

julia> combine(df, AsTable(:) => ByRow(x -> (mean=mean(x), std=std(x))) => :stats,                AsTable(:) => ByRow(x -> (mean=mean(x), std=std(x))) => AsTable) 3×3 DataFrame  Row │ stats                    mean     std      │ NamedTup…                Float64  Float64 ─────┼───────────────────────────────────────────    1 │ (mean = 4.0, std = 3.0)      4.0      3.0    2 │ (mean = 5.0, std = 3.0)      5.0      3.0    3 │ (mean = 6.0, std = 3.0)      6.0      3.0

julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),                       b=repeat([2, 1], outer=[4]),                       c=1:8);

julia> gd = groupby(df, :a);

julia> combine(gd, :c => sum, nrow) 4×3 DataFrame  Row │ a      c_sum  nrow      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     1      6      2    2 │     2      8      2    3 │     3     10      2    4 │     4     12      2

julia> combine(gd, :c => sum, nrow, ungroup=false) GroupedDataFrame with 4 groups based on key: a First Group (1 row): a = 1  Row │ a      c*sum  nrow      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     1      6      2 ⋮ Last Group (1 row): a = 4  Row │ a      c*sum  nrow      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     4     12      2

julia> combine(gd) do d # do syntax for the slower variant            sum(d.c)        end 4×2 DataFrame  Row │ a      x1      │ Int64  Int64 ─────┼──────────────    1 │     1      6    2 │     2      8    3 │     3     10    4 │     4     12

julia> combine(gd, :c => (x -> sum(log, x)) => :sum*log*c) # specifying a name for target column 4×2 DataFrame  Row │ a      sum*log*c      │ Int64  Float64 ─────┼──────────────────    1 │     1    1.60944    2 │     2    2.48491    3 │     3    3.04452    4 │     4    3.46574

julia> combine(gd, [:b, :c] .=> sum) # passing a vector of pairs 4×3 DataFrame  Row │ a      b*sum  c*sum      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     1      4      6    2 │     2      2      8    3 │     3      4     10    4 │     4      2     12

julia> combine(gd) do sdf # dropping group when DataFrame() is returned           sdf.c[1] != 1 ? sdf : DataFrame()        end 6×3 DataFrame  Row │ a      b      c      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     2      1      2    2 │     2      1      6    3 │     3      2      3    4 │     3      2      7    5 │     4      1      4    6 │     4      1      8

```

# 自動スプラッティング、リネーム、およびキープキー

```

jldoctest julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),                       b=repeat([2, 1], outer=[4]),                       c=1:8);

julia> gd = groupby(df, :a);

julia> combine(gd, :b => :b1, :c => :c1, [:b, :c] => +, keepkeys=false) 8×3 DataFrame  Row │ b1     c1     b*c*+      │ Int64  Int64  Int64 ─────┼─────────────────────    1 │     2      1      3    2 │     2      5      7    3 │     1      2      3    4 │     1      6      7    5 │     2      3      5    6 │     2      7      9    7 │     1      4      5    8 │     1      8      9

```

# ブロードキャスティングと列の拡張

```

jldoctest julia> df = DataFrame(a=repeat([1, 2, 3, 4], outer=[2]),                       b=repeat([2, 1], outer=[4]),                       c=1:8);

julia> gd = groupby(df, :a);

julia> combine(gd, :b, AsTable([:b, :c]) => ByRow(extrema) => [:min, :max]) 8×4 DataFrame  Row │ a      b      min    max      │ Int64  Int64  Int64  Int64 ─────┼────────────────────────────    1 │     1      2      1      2    2 │     1      2      2      5    3 │     2      1      1      2    4 │     2      1      1      6    5 │     3      2      2      3    6 │     3      2      2      7    7 │     4      1      1      4    8 │     4      1      1      8

julia> combine(gd, [:b, :c] .=> Ref) # preventing vector from being spread across multiple rows 4×3 DataFrame  Row │ a      b*Ref      c*Ref      │ Int64  SubArray…  SubArray… ─────┼─────────────────────────────    1 │     1  [2, 2]     [1, 5]    2 │     2  [1, 1]     [2, 6]    3 │     3  [2, 2]     [3, 7]    4 │     4  [1, 1]     [4, 8]

julia> combine(gd, AsTable(Not(:a)) => Ref) # protecting result 4×2 DataFrame  Row │ a      b*c*Ref      │ Int64  NamedTup… ─────┼─────────────────────────────────    1 │     1  (b = [2, 2], c = [1, 5])    2 │     2  (b = [1, 1], c = [2, 6])    3 │     3  (b = [2, 2], c = [3, 7])    4 │     4  (b = [1, 1], c = [4, 8])

julia> combine(gd, :, AsTable(Not(:a)) => sum, renamecols=false) 8×4 DataFrame  Row │ a      b      c      b_c      │ Int64  Int64  Int64  Int64 ─────┼────────────────────────────    1 │     1      2      1      3    2 │     1      2      5      7    3 │     2      1      2      3    4 │     2      1      6      7    5 │     3      2      3      5    6 │     3      2      7      9    7 │     4      1      4      5    8 │     4      1      8      9 ```
