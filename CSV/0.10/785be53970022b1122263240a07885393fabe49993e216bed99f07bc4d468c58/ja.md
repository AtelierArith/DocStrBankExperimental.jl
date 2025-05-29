`CSV.read(source, sink::T; kwargs...)` => T

区切り文字付きファイルまたはファイル群を読み込み、`sink`関数を使用して直接マテリアライズします。`DataFrame`のような特定のシンクに対して列の過剰なコピーを避けることができます。

# 例

```
julia> using CSV, DataFrames

julia> path = tempname();

julia> write(path, "a,b,c\n1,2,3");

julia> CSV.read(path, DataFrame)
1×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      2      3

julia> CSV.read(path, DataFrame; header=false)
2×3 DataFrame
 Row │ Column1  Column2  Column3
     │ String1  String1  String1
─────┼───────────────────────────
   1 │ a        b        c
   2 │ 1        2        3
```

# 引数

## ファイルレイアウトオプション:

  * `header=1`: 列名がどのように決定されるか; `Integer`として与えられた場合、列名を解析する行を示します; `AbstractVector{<:Integer}`として与えられた場合、列名として結合される行のセットを示します; `Vector{Symbol}`または`Vector{String}`は列名を明示的に指定します（データセットの列数と一致する必要があります）。データセットに列名がない場合は、`Vector`として提供するか、`header=0`または`header=false`を設定すると、列名が自動生成されます（`Column1`、`Column2`など）。行番号のヘッダーと`comment`または`ignoreemptyrows`が提供されている場合、ヘッダー行は行番号の*後*の最初の非コメント/非空行になります。つまり、提供された行番号がコメント行である場合、ヘッダー行は実際には次の非コメント行になります。
  * `normalizenames::Bool=false`: 列名を有効なJulia識別子シンボルに「正規化」するかどうか; `tbl.col1`の`getproperty`構文を使用する場合や、行を反復処理し、`getproperty`を介して行の列値にアクセスする場合（例: `row.col1`）に便利です。
  * `skipto::Integer`: csvファイル内のデータが開始する行を指定します; デフォルトでは、`header`行の次の行が使用されます。`header=0`の場合、1行目がデータの開始と見なされます; `skipto`引数を提供しても`header`引数には影響しません。行番号`skipto`と`comment`または`ignoreemptyrows`が提供されている場合、データ行は行番号の*後*の最初の非コメント/非空行になります。つまり、提供された行番号がコメント行である場合、データ行は実際には次の非コメント行になります。
  * `footerskip::Integer`: ファイルの末尾で解析をスキップする行数。コメント行（`comment`キーワード引数を参照）*は*`footerskip`で提供された行数にはカウントされず、パーサーによって完全に無視されます。
  * `transpose::Bool`: csvファイルを「転置」して読み取ります。つまり、各列が行として解析されます。
  * `comment::String`: それで始まる行を解析中にスキップさせる文字列。行番号のヘッダーまたは`skipto`と`comment`が提供されている場合、ヘッダー/データ行は行番号の*後*の最初の非コメント/非空行になります。つまり、提供された行番号がコメント行である場合、ヘッダー/データ行は実際には次の非コメント行になります。
  * `ignoreemptyrows::Bool=true`: ファイル内の空行を無視するかどうか（`false`の場合、その空行に対して各列に`missing`が割り当てられます）。
  * `select`: `Integer`、`Symbol`、`String`、または`Bool`の`AbstractVector`、または形式`(i, name) -> keep::Bool`の「セレクタ」関数; コレクション内の列またはセレクタ関数が`true`を返す列のみが解析され、結果の`CSV.File`でアクセス可能になります。`select`内の無効な値は無視されます。
  * `drop`: `select`の逆; `Integer`、`Symbol`、`String`、または`Bool`の`AbstractVector`、または形式`(i, name) -> drop::Bool`の「ドロップ」関数; コレクション内の列またはドロップ関数が`true`を返す列は、結果の`CSV.File`で無視されます。`drop`内の無効な値は無視されます。
  * `limit`: csvファイル内で解析する行数を制限するための`Integer`; `skipto`と組み合わせて、ファイル内の特定の連続したチャンクを読み取るために使用します; 複数のスレッドが解析に使用される大きなファイルの場合、`limit`引数は正確な行数の解析をもたらさない場合があります; 必要に応じて正確な制限を確保するために`ntasks=1`を使用してください。
  * `buffer_in_memory`: `Bool`、デフォルトは`false`で、`Cmd`、`IO`、またはgzippedソースがメモリ内で読み取られるか、一時ファイルを使用するかを制御します。
  * `ntasks::Integer=Threads.nthreads()`: [`CSV.Rows`には適用されません] マルチスレッドで解析されたファイルの場合、ファイルを同時にチャンクで読み取るために生成されるタスクの数を制御します; デフォルトはJuliaが開始されたスレッドの数です（すなわち、`JULIA_NUM_THREADS`環境変数または`julia -t N`）; `ntasks=1`を設定すると、`Threads.@spawn`への呼び出しを回避し、メインスレッドでファイルを直列に読み取ります; 小さなファイルの場合はデフォルトで単一スレッドが使用されます（< 5_000セル）。
  * `rows_to_check::Integer=30`: [`CSV.Rows`には適用されません] マルチスレッドで解析されたファイルは`ntasks`の数の等しいチャンクに分割されます; `rows_to_check`は、解析が正しく有効な行を見つけたことを確認するためにチェックされる行数を制御します; 非常に大きな引用テキストフィールドを持つ特定のファイルの場合、`lines_to_check`はこれらの行を正しく見つけるために高くする必要があるかもしれません（10、30など）。
  * `source`: [`CSV.File`への入力ベクトルにのみ適用されます] `Symbol`、`String`、または`Symbol`または`String`から`Vector`への`Pair`。単一の`Symbol`または`String`として、解析された列に追加される列名を提供し、その列の値は入力の「名前」（通常はファイル名）になります。`Pair`として、ペアの2番目の部分は、入力の数と一致する長さの値の`Vector`である必要があり、各値は自動追加列のその入力の値の入力名の代わりに使用されます。

## 解析オプション:

  * `missingstring`: `nothing`、`String`、または`Vector{String}`のいずれかで、`missing`として解析されるセントinel値として使用されます; `nothing`が渡された場合、セントinel/欠損値は解析されません; デフォルトでは、`missingstring=""`で、これは空のフィールド（2つの連続した区切り文字）のみが`missing`と見なされます。
  * `delim=','`: ファイル内の列がどのように区切られているかを示す`Char`または`String`; 引数が提供されていない場合、解析はファイルの最初の10行で最も一貫した区切り文字を検出しようとします。
  * `ignorerepeated::Bool=false`: 解析中に連続した（連続的な）区切り文字を無視するかどうか; セル間の区切りパディングを持つ固定幅ファイルに便利です。
  * `quoted::Bool=true`: 解析がセルの開始/終了で`quotechar`をチェックするべきかどうか。
  * `quotechar='"'`、`openquotechar`、`closequotechar`: テキスト区切り文字や改行文字を含む可能性のある引用フィールドを示す`Char`（または異なる開始および終了文字）。
  * `escapechar='"'`: 引用フィールド内の引用文字をエスケープするために使用される`Char`。
  * `dateformat::Union{String, Dates.DateFormat, Nothing, AbstractDict}`: ファイル全体のDate/DateTime列がどのようにフォーマットされるかを示す日付フォーマット文字列; `AbstractDict`として与えられた場合、キーに対応するDate/DateTime列がどのようにフォーマットされるかを示す日付フォーマット文字列。Dictは列インデックス`Int`または名前`Symbol`または`String`をその列のフォーマット文字列にマッピングできます。
  * `decimal='.'`: 浮動小数点数の小数がどのように区切られているかを示す`Char`、すなわち`3.14`は`'.'`を使用し、`3,14`はカンマ`','`を使用します。
  * `groupmark=nothing`: 数字のグループ化マークを示す単一バイト文字をオプションで指定します。これにより、例えば千の区切り文字（`1,000.00`）を持つ数字の解析が可能になります。
  * `truestrings`、`falsestrings`: `true`または`false`の値がどのように表現されるかを示す`Vector{String}`; デフォルトでは`"true", "True", "TRUE", "T", "1"`が`true`を検出するために使用され、`"false", "False", "FALSE", "F", "0"`が`false`を検出するために使用されます; `1`と`0`の値のみを持つ列は、`types`キーワード引数を介して明示的に`Bool`を要求しない限り、デフォルトで`Int64`列型になります。
  * `stripwhitespace=false`: `true`の場合、文字列値の前後の空白が削除されます。列名も含まれます。

## 列型オプション:

  * `types`: 列型に使用される単一の`Type`、`AbstractVector`または`AbstractDict`、または形式`(i, name) -> Union{T, Nothing}`の関数; 単一の`Type`が提供された場合、*すべての*列はその単一の型で解析されます; `AbstractDict`は列インデックス`Integer`または名前`Symbol`または`String`を型にマッピングできます。つまり、`Dict(1=>Float64)`は最初の列を`Float64`として設定し、`Dict(:column1=>Float64)`は`column1`という名前の列を`Float64`に設定し、`Dict("column1"=>Float64)`は`column1`を`Float64`に設定します; `Vector`が提供された場合、提供された列数または`header`で検出された列数と一致する必要があります。関数が提供された場合、列インデックスと名前を引数として受け取り、その列の望ましい列型を返す必要があります。また、解析中に列の型を検出するために`nothing`を返すこともできます。
  * `typemap::IdDict{Type, Type}`: すべてのインスタンスで別の型に置き換えるべき型のマッピング。例えば、`Dict(Float64=>String)`は、検出されたすべての`Float64`列を`String`として解析します; マッピングされる型は「標準」型のみで、`Int64`、`Float64`、`Date`、`DateTime`、`Time`、および`Bool`が許可されます。これらの型の列が「検出」されると、指定された型にマッピングされます。
  * `pool::Union{Bool, Real, AbstractVector, AbstractDict, Function, Tuple{Float64, Int}}=(0.2, 500)`: [`CSV.Rows`ではサポートされていません] 列が`PooledArray`として構築されるかどうかを制御します; `true`の場合、検出されたすべての列が`String`としてプールされます; あるいは、`String`列がプールされるべきユニーク値の割合を示すしきい値を指定します（つまり、列内のユニークな文字列の数が25%未満の場合、`pool=0.25`、それはプールされます）。`(0.2, 500)`のように`Tuple{Float64, Int}`として提供された場合、最初のタプル要素（`0.2`）としてのパーセントのカーディナリティしきい値と、ユニークな値の上限（`500`）を示します。この列はプールされます; これはデフォルトです（`pool=(0.2, 500)`）。`AbstractVector`として提供された場合、各要素は`Bool`、`Real`、または`Tuple{Float64, Int}`である必要があり、要素の数はデータセット内の列の数と一致する必要があります; `AbstractDict`の場合、列インデックス`Integer`または列名`Symbol`または`String`として与えられた個々の列に対して`Bool`、`Real`、または`Tuple{Float64, Int}`値を提供できます。関数が提供された場合、列インデックスと名前を2つの引数として受け取り、各列に対して`Bool`、`Real`、`Tuple{Float64, Int}`、または`nothing`を返す必要があります。
  * `downcast::Bool=false`: `Int64`として検出された列が、`Int8`、`Int16`、`Int32`などの最小の整数型に「ダウンキャスト」されるかどうかを制御します。
  * `stringtype=InlineStrings.InlineString`: 検出された文字列列が最終的にどのように返されるかを制御します; デフォルトは`InlineString`で、これは文字列データを固定サイズのプリミティブ型に格納し、過剰なヒープメモリ使用を回避するのに役立ちます; 列に32バイトを超える値がある場合、デフォルトで`String`になります。`String`が渡された場合、すべての文字列列は通常の`String`値になります。`PosLenString`が渡された場合、文字列列は`PosLenStringVector`として返されます。これは、元のファイルデータへの「ビュー」として機能する特別な「遅延」`AbstractVector`です。これにより、最も効率的な解析時間が得られますが、`PosLenStringVector`の「ビュー」性質により、`push!`、`append!`、または`setindex!`のような操作はサポートされません。また、元の入力データセットソースへの参照を保持するため、例えば、基盤となるファイルを変更または削除しようとすると失敗する可能性があります。
  * `strict::Bool=false`: 無効な値が解析エラーを引き起こすべきか、`missing`に置き換えられるべきか。
  * `silencewarnings::Bool=false`: `strict=false`の場合、無効な値の警告を抑制するかどうか。
  * `maxwarnings::Int=100`: 解析中に`maxwarnings`の数を超える警告が印刷された場合、デフォルトでさらなる警告は抑制されます; マルチスレッド解析の場合、各解析タスクは最大`maxwarnings`まで印刷します。
  * `debug::Bool=false`: `true`を渡すと、データセットが解析される間に多くの情報印刷が行われます; 問題を報告したり、データセットが解析される間に何が起こっているのかを理解するのに役立ちます。
  * `validate::Bool=true`: `types`、`dateformat`、および`pool`キーワードで指定された列が実際にデータに存在することを検証するかどうか。`false`の場合、検証は行われず、`types`/`dateformat`/`pool`がデータに実際に見つからない列の設定を指定してもエラーは発生しません。

## 反復オプション:

  * `reusebuffer=false`: [`CSV.Rows`にのみサポートされています] 反復中に、各反復で単一の行バッファを割り当てて再利用するかどうか; 各行が一度だけ反復され、再利用されない場合にのみ使用します（例えば、`collect(CSV.Rows(file))`を行う場合、このオプションを使用するのは安全ではありません。なぜなら、現在反復されている行のみが「有効」だからです）。
