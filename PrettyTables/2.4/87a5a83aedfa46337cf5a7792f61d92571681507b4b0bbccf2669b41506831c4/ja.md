```
pretty_table([io::IO | String | HTML,] table;  kwargs...)
```

`table`を`io`に印刷します。

`io`が省略された場合、デフォルトは`stdout`です。`io`の代わりに`String`が渡された場合、印刷されたテーブルを含む`String`が関数によって返されます。`io`の代わりに`HTML`が渡された場合、印刷されたテーブルを含む`HTML`オブジェクトが返されます。

印刷時に、`table`が**Tables.jl** APIに準拠しているかどうかが確認されます。準拠している場合、このインターフェースがテーブルの印刷に使用されます。準拠していない場合、次のタイプのみがサポートされます：

1. `AbstractVector`：任意のベクターを印刷できます。
2. `AbstractMatrix`：任意の行列を印刷できます。
3. `Dict`：任意の`Dict`を印刷できます。この場合、特別なキーワード`sortkeys`を使用して、ユーザーが辞書をキーをソートして印刷するかどうかを選択できます。`false`の場合、要素は`keys`および`values`関数によって返されるのと同じ順序で印刷されます。これは、キーがソート可能であることを前提としています。そうでない場合、エラーがスローされます。

# キーワード

  * `alignment::Union{Symbol, Vector{Symbol}}`：列の整列を選択します（`Alignment`セクションを参照）。
  * `backend::Union{Symbol, T_BACKENDS}`：テーブルを印刷するために使用されるバックエンドを選択します（`Back End`セクションを参照）。`kwargs...`の追加設定は、選択されたバックエンドに依存します。
  * `cell_alignment::Union{Nothing, Dict{Tuple{Int, Int}, Symbol}, Function, Tuple}`：セル`(i, j)`の整列を`f`によって返される値にオーバーライドする関数のタプルです。単一の関数である場合、1つの整列関数のみが必要であると仮定され、`nothing`の場合はセル整列の変更は行われません。関数`f`が`Alignment`セクションに示されている有効な整列シンボルを返さない場合、それは破棄されます。便利のために、セル`(i, j)`の整列を`a`にオーバーライドする型`(i, j) => a`の辞書でも構いません。`a`は`Alignment`セクションに指定されたようにシンボルでなければなりません。 (**デフォルト** = `nothing`)

!!! note
    `cell_alignment`に複数の整列関数が渡された場合、関数はタプルの同じ順序で評価されます。各セルに対して有効な整列シンボルを返す最初のものが適用され、残りは破棄されます。


  * `cell_first_line_only::Bool`：`true`の場合、各セルの最初の行のみが印刷されます。 (**デフォルト** = `false`)
  * `compact_printing::Bool`：データを印刷する際に`：compact`オプションが使用されるかどうかを選択します。 (**デフォルト** = `true`)
  * `formatters::Union{Nothing, Function, Tuple}`：`Formatters`セクションを参照してください。
  * `header::Union{Symbol, Vector{Symbol}}`：ヘッダーはベクターのタプルでなければなりません。それぞれはテーブルの列数と同じ数の要素を持たなければなりません。最初のベクターはヘッダーと見なされ、他はサブヘッダーです。`nothing`の場合、タイプに基づいてデフォルト値が使用されます。単一のベクターが渡された場合、それはヘッダーと見なされます。 (**デフォルト** = `nothing`)
  * `header_alignment::Union{Symbol, Vector{Symbol}}`：ヘッダー列の整列を選択します（`Alignment`セクションを参照）。特定の列の整列を指定するシンボルが`:s`の場合、その列の`alignment`キーワードの同じ整列が使用されます。 (**デフォルト** = `:s`)
  * `header_cell_alignment::Union{Nothing, Dict{Tuple{Int, Int}, Symbol}, Function, Tuple}`：このキーワードは`cell_alignment`と同じ構造を持ちますが、この場合はヘッダーで動作します。したがって、`(i, j)`はヘッダーとサブヘッダーを含むヘッダーマトリックスのセルになります。これは、関数内の`data`フィールドが`header`キーワードに渡されたのと同じ値であることを意味します。 (**デフォルト** = `nothing`)

!!! note
    `header_cell_alignment`に複数の整列関数が渡された場合、関数はタプルの同じ順序で評価されます。各セルに対して有効な整列シンボルを返す最初のものが適用され、残りは破棄されます。


  * `limit_printing::Bool`：`true`の場合、セルは`IOContext`のプロパティ`:limit => true`を使用して変換されます。 (**デフォルト** = `true`)
  * `max_num_of_columns::Int`：レンダリングされるテーブル列の最大数。0未満の場合、すべての列がレンダリングされます。 (**デフォルト** = -1)
  * `max_num_of_rows::Int`：レンダリングされるテーブル行の最大数。0未満の場合、すべての行がレンダリングされます。 (**デフォルト** = -1)
  * `renderer::Symbol`：オブジェクトを文字列に変換するために使用される関数を示すシンボル。`:print`を使用して`print`関数を使用するか、`:show`を使用して`show`関数を使用します。この選択はテーブルデータにのみ適用されます。ヘッダー、サブヘッダー、および行名列は常に印刷されます。 (**デフォルト** = `:print`)
  * `row_labels::Union{Nothing, AbstractVector}`：テーブルの左側に追加される行ラベルを含むベクター。`nothing`の場合、行ラベルの列は表示されません。このベクターのサイズはテーブルの行数と一致する必要があります。 (**デフォルト** = `nothing`)
  * `row_label_alignment::Symbol`：行ラベル列の整列を選択します（`Alignment`セクションを参照）。
  * `row_label_column_title::AbstractString`：行ラベルの列のタイトル。 (**デフォルト** = "")
  * `row_number_column_title::AbstractString`：行番号の列のタイトル。 (**デフォルト** = "Row")
  * `show_header::Bool`：`true`の場合、ヘッダーが印刷されます。すべてのキーワードとヘッダーおよびサブヘッダーに関連するパラメータは無視されます。 (**デフォルト** = `false`)
  * `show_row_number::Bool`：`true`の場合、新しい列が印刷され、行番号が表示されます。 (**デフォルト** = `false`)
  * `show_subheader::Bool`：`true`の場合、サブヘッダーが印刷されます。すなわち、ヘッダーにはヘッダーとサブヘッダーの両方が含まれます。このオプションは`show_header = false`の場合には影響しません。 (**デフォルト** = `true`)
  * `title::AbstractString`：テーブルのタイトル。空の場合、タイトルは印刷されません。 (**デフォルト** = "")
  * `title_alignment::Symbol`：タイトルの整列。これは`Alignment`セクションで説明されているようにシンボルでなければなりません。この引数はLaTeXバックエンドでは無視されます。 (**デフォルト** = :l)

!!! note
    すべてのバックエンドには、テーブル印刷形式を指定するキーワード`tf`があります。したがって、キーワード`backend`が存在しない場合、または`nothing`の場合、バックエンドは自動的にキーワード`tf`のタイプから推測されます。この場合、`tf`も存在しない場合、最初の引数として`HTML`が渡されない限り、テキストバックエンドにフォールバックします。この場合、デフォルトのバックエンドはHTMLに設定されます。


`String`が使用される場合、キーワード`color`は、テーブルが色付きまたは色なしの文字列に変換されるかどうかを選択します。デフォルト値は`false`です。このオプションはテキストバックエンドでのみ効果があります。

# 整列

キーワード`alignment`は`Symbol`または`Symbol`のベクターであることができます。

シンボルである場合、次の動作があります：

  * `:l`または`:L`：すべての列のテキストは左揃えになります。
  * `:c`または`:C`：すべての列のテキストは中央揃えになります。
  * `:r`または`:R`：すべての列のテキストは右揃えになります。
  * それ以外の場合はデフォルトで`:r`になります。

ベクターである場合、`data`の列数と同じ数のシンボルを持たなければなりません。ベクター内の*i*番目のシンボルは、前述の同じシンボルを使用して*i*番目の列の整列を指定します。

!!! note
    HTMLバックエンドでは、ユーザーは`:n`または`:N`を選択して、整列注釈なしでセルを印刷できます。


---

# テキストバックエンド

このバックエンドはテキストテーブルを生成します。このバックエンドは`backend = :text`を選択することで使用できます。

## キーワード

  * `alignment_anchor_fallback::Symbol`：このキーワードは、正規表現整列アンカーを使用する際に、一致が見つからない場合の行整列を制御します。`:l`の場合、行の左側がアンカーに整列されます。`:c`の場合、行の中央がアンカーに整列されます。それ以外の場合、行の末尾がアンカーに整列されます。 (**デフォルト** = `:l`)
  * `alignment_anchor_fallback_override::Dict{Int, Symbol}`：特定の列の`fallback_alignment_anchor`の動作をオーバーライドするための`Dict{Int, Symbol}`。例：`Dict(3 => :c)`は、列3の`：c`のフォールバック整列アンカーの動作を変更します。
  * `alignment_anchor_regex::Dict{Int, AbstractVector{Regex}}`：列（キー）の値を整列させるために使用される正規表現のセットを持つ辞書`Dict{Int, AbstractVector{Regex}}`。各セルの各行の最初の正規表現一致（またはアンカー）での文字が整列されます。正規表現の一致は、ベクターに表示される正規表現の順序で検索されます。正規表現の一致は、フォーマッタを含む文字列へのセル変換の後に適用されます。特定の行に一致が見つからない場合、その行の整列は`alignment_anchor_fallback`および`alignment_anchor_fallback_override`オプションに依存します。キー`0`が存在する場合、関連する正規表現はすべての列を整列させるために使用されます。この場合、他のすべてのキーは無視されます。例：`Dict(2 => [r"\."])`は、2列目のセルの小数点を整列させます。 (**デフォルト** = `Dict{Int, Vector{Regex}}()`)
  * `autowrap::Bool`：`true`の場合、テキストは列に収まるようにスペースで折り返されます。この関数は`linebreaks = true`を必要とし、列は固定サイズでなければなりません（`columns_width`を参照）。
  * `body_hlines::Vector{Int}`：追加の水平線を描画する行番号を示す`Int`のベクター。0未満および印刷された行数以上の番号は無視されます。このベクターは`hlines`のものに追加されますが、ここでのインデックスはボディの印刷された行に関連しています。したがって、`1`が`body_hlines`に追加されると、最初のデータ行の後に水平線が描画されます。 (**デフォルト** = `Int[]`)
  * `body_hlines_format::Union{Nothing, NTuple{4, Char}}`：`body_hlines`によって描画される水平線の形式を指定する4文字のタプル。文字は左の交差点、中間の交差点、右の交差点、および行でなければなりません。`nothing`の場合、`tf`で指定されたのと同じ形式が使用されます。 (**デフォルト** = `nothing`)
  * `columns_width::Union{Int, AbstractVector{Int}}`：各列の幅を指定する整数のセット。幅が0以下の場合、列内の大きなセルに合わせて自動的に計算されます。単一の整数の場合、この数はすべての列のサイズとして使用されます。 (**デフォルト** = 0)
  * `crop::Symbol`：データが利用可能な表示サイズよりも大きい場合の印刷動作を選択します（`display_size`を参照）。`：both`は垂直および水平方向の両方で切り取る、`：horizontal`は水平方向のみで切り取る、`：vertical`は垂直方向のみで切り取る、または`：none`はデータを全く切り取らないことを意味します。`io`が`:limit => true`の場合、デフォルトで`crop`は`:both`に設定されます。それ以外の場合、デフォルトで`:none`に設定されます。
  * `crop_subheader::Bool`：`true`の場合、サブヘッダーのサイズは列サイズを計算する際に考慮されません。したがって、印刷アルゴリズムはスペースを節約するためにそれを切り取ることができます。ユーザーが固定列幅を選択した場合、これは影響しません。 (**デフォルト** = `false`)
  * `continuation_row_alignment::Symbol`：継続行のセルの整列を定義するシンボル。この行はテーブルが垂直に切り取られた場合に印刷されます。 (**デフォルト** = `:c`)
  * `display_size::Tuple{Int, Int}`：テーブルを印刷するために利用可能な表示サイズ（行数、列数）を定義する2つの整数のタプル。これは、キーワード`crop`の値に応じてデータを切り取るために使用されます。次元が正でない場合、無制限として扱われます。 (**デフォルト** = `displaysize(io)`)
  * `ellipsis_line_skip::Integer`：省略記号が表示される行数を定義する整数。 (**デフォルト** = 0)
  * `equal_columns_width::Bool`：`true`の場合、すべての列は同じ幅になります。 (**デフォルト** = `false`)
  * `highlighters::Union{Highlighter, Tuple}`：`Highlighter`のインスタンスまたはテキストハイライターのリストを含むタプル（`Text highlighters`セクションを参照）。
  * `hlines::Union{Nothing, Symbol, AbstractVector}`：この変数は水平線が描画される場所を制御します。`nothing`、`:all`、`:none`または整数のベクターであることができます。 (**デフォルト** = `nothing`)

      * `nothing`の場合、デフォルトで、設定は変数`tf`のテーブル形式から取得されます（[`TextFormat`](@ref)を参照）。
      * `:all`の場合、すべての水平線が描画されます。
      * `:none`の場合、水平線は描画されません。
      * 整数のベクターの場合、ベクター内の行の後にのみ水平線が描画されます。最上部の線は`0`が`hlines`に含まれている場合に描画され、ヘッダーとサブヘッダーは1行として考慮されます。さらに、この変数の行番号は**印刷された行**に関連していることを重要です。したがって、`show_header`オプションによってヘッダーを抑制する影響を受けます。最後に、便利のために、最上部と最下部の線はそれぞれこのベクターにシンボル`:begin`と`:end`を追加することで描画できます。

!!! info
    `body_hlines`の値はこのベクターに追加されます。したがって、`hlines`が`:none`であっても水平線を描画できます。


  * `linebreaks::Bool`：`true`の場合、`\n`はセル内で行を折り返します。 (**デフォルト** = `false`)
  * `maximum_columns_width::Union{Int, AbstractVector{Int}}`：各列の最大幅を指定する整数のセット。幅が0以下の場合、無視されます。単一の整数の場合、この数はすべての列の最大幅として使用されます。`columns_width`パラメータはこのパラメータよりも優先されます。 (**デフォルト** = 0)
  * `minimum_columns_width::Union{Int, AbstractVector{Int}}`：各列の最小幅を指定する整数のセット。幅が0以下の場合、無視されます。単一の整数の場合、この数はすべての列の最小幅として使用されます。`columns_width`パラメータはこのパラメータよりも優先されます。 (**デフォルト** = 0)
  * `newline_at_end::Bool`：`false`の場合、テーブルは改行文字で終わりません。 (**デフォルト** = `true`)
  * `overwrite::Bool`：`true`の場合、印刷されたテーブルの行数と同じ数の行が出力`io`から削除されます。これを使用して、表示を継続的に更新できます。 (**デフォルト** = `false`)
  * `reserved_display_lines::Int`：出力を垂直に切り取る際に印刷の最初に残す行数。タイトルを表示するために必要な行数は自動的に計算されます。 (**デフォルト** = 0)
  * `row_number_alignment::Symbol`：行番号列の整列を選択します（`Alignment`セクションを参照）。 (**デフォルト** = `:r`)
  * `show_omitted_cell_summary::Bool`：`true`の場合、テーブルの後に省略された列と行の数を含む要約が印刷されます。 (**デフォルト** = `true`)
  * `tf::TextFormat`：テーブルを印刷するために使用されるテーブル形式（[`TextFormat`](@ref)を参照）。 (**デフォルト** = `tf_unicode`)
  * `title_autowrap::Bool`：`true`の場合、タイトルテキストはタイトルサイズを考慮して折り返されます。そうでない場合、タイトルサイズを超える行は切り取られます。 (**デフォルト** = `false`)
  * `title_same_width_as_table::Bool`：`true`の場合、タイトル幅はテーブルの幅と一致します。そうでない場合、タイトルサイズは表示幅と等しくなります。 (**デフォルト** = `false`)
  * `vcrop_mode::Symbol`：この変数は垂直切り取りの動作を定義します。`:bottom`の場合、必要に応じてデータは下部で切り取られます。一方、`:middle`の場合、必要に応じてデータは中央で切り取られます。 (**デフォルト** = `:bottom`)
  * `vlines::Union{Nothing, Symbol, AbstractVector}`：この変数は垂直線が描画される場所を制御します。`nothing`、`:all`、`:none`または整数のベクターであることができます。 (**デフォルト** = `nothing`)

      * `nothing`の場合、デフォルトで、設定は変数`tf`のテーブル形式から取得されます（[`TextFormat`](@ref)を参照）。
      * `:all`の場合、すべての垂直線が描画されます。
      * `:none`の場合、垂直線は描画されません。
      * 整数のベクターの場合、ベクター内の列の後にのみ垂直線が描画されます。左の線は`0`が`vlines`に含まれている場合に描画されます。さらに、この変数の列番号は**印刷された列**に関連していることを重要です。したがって、`row_labels`および`show_row_number`オプションの影響を受けます。最後に、便利のために、左と右の垂直線はそれぞれこのベクターにシンボル`:begin`と`:end`を追加することで描画できます。

クレヨンに関連する次のキーワードが出力装飾をカスタマイズするために利用可能です：

  * `border_crayon::Crayon`：境界を印刷するためのクレヨン。
  * `header_crayon::Union{Crayon, Vector{Crayon}}`：ヘッダーを印刷するためのクレヨン。
  * `omitted_cell_summary_crayon::Crayon`：省略されたセルの要約を印刷するために使用されるクレヨン。
  * `row_label_crayon::Crayon`：行ラベルを印刷するためのクレヨン。
  * `row_label_header_crayon::Crayon`：行ラベルの列のヘッダーを印刷するためのクレヨン。
  * `row_number_header_crayon::Crayon`：行番号の列のヘッダーのためのクレヨン。
  * `subheader_crayon::Union{Crayon, Vector{Crayon}}`：サブヘッダーを印刷するためのクレヨン。
  * `text_crayon::Crayon`：デフォルトテキストを印刷するためのクレヨン。
  * `title_crayon::Crayon`：タイトルを印刷するためのクレヨン。

`header_crayon`および`subheader_crayon`は`Crayon`または`Vector{Crayon}`であることができます。最初のケースでは、`Crayon`はすべての要素に適用されます。2番目の場合、各要素は独自のクレヨンを持つことができますが、ベクターの長さはデータの列数と等しくなければなりません。

## クレヨン

`Crayon`は、端末に印刷されるテキストのスタイルを処理するオブジェクトです。これは、パッケージ[Crayons.jl](https://github.com/KristofferC/Crayons.jl)で定義されています。前景色、背景色、太字テキストなど、スタイルをカスタマイズするための多くのオプションがあります。

`Crayon`は2つの異なる方法で作成できます：

```julia-repl
julia> Crayon(foreground = :blue, background = :black, bold = :true)

julia> crayon"blue bg:black bold"
```

詳細については、パッケージのドキュメントを参照してください。

## テキストハイライター

ハイライターのセットは、`highlighters`キーワードに`Tuple`として渡すことができます。各ハイライターは、次の3つのフィールドを含む`Highlighter`構造のインスタンスです：

  * `f::Function`：`f(data, i, j)`というシグネチャを持つ関数で、`data`内の要素`(i, j)`をハイライトする必要がある場合は`true`を返し、そうでない場合は`false`を返します。
  * `fd::Function`：`f(h,data,i,j)`というシグネチャを持つ関数で、`h`はハイライターです。この関数は、ハイライトする必要があるセルに適用される`Crayon`を返さなければなりません。
  * `crayon::Crayon`：デフォルトの`fd`が使用される場合にハイライトされたセルに適用される`Crayon`。

関数`f`は次のシグネチャを持ちます：

```
f(data, i, j)
```

ここで、`data`は印刷されているデータへの参照であり、`i`と`j`はテストされている要素の座標です。この関数が`true`を返すと、セル`(i, j)`がハイライトされます。

関数`f`が`true`を返すと、関数`fd(h, data, i, j)`が呼び出され、ハイライトされるセルに適用される`Crayon`を返さなければなりません。

ハイライターは次の3つのヘルパーを使用して構築できます：

```
Highlighter(f::Function; kwargs...)
```

ここでは、`kwargs`内のキーワードを使用して`Crayon`を構築し、ハイライトされたセルに適用します。

```
Highlighter(f::Function, crayon::Crayon)
```

ここでは、ハイライトされたセルに`crayon`を適用します。

```
Highlighter(f::Function, fd::Function)
```

ここでは、ハイライトされたセルに関数`fd`によって返された`Crayon`を適用します。

!!! info
    単一のハイライターが必要な場合は、`Tuple`内に入れずに`highlighter`キーワードに直接渡すことができます。


!!! note
    複数のハイライターが要素`(i, j)`に対して有効な場合、適用されるスタイルは、タプル`highlighters`内の順序を考慮して最初の一致と等しくなります。


!!! note
    ハイライターが[Formatters](@ref)と一緒に使用される場合、フォーマットの変更はハイライター関数`f`に渡されるパラメータ`data`に**影響しません**。常に元の未フォーマットの値が受け取られます。


---

# HTMLバックエンド

このバックエンドはHTMLテーブルを生成します。このバックエンドは`backend = Val(:html)`を選択することで使用できます。

## キーワード

  * `allow_html_in_cells::Bool`：デフォルトでは、`<`、`>`、`"`などの特殊文字はHTMLバックエンドで置き換えられ、有効なコードが生成されます。ただし、このアルゴリズムはセル内でのHTMLコードの使用をブロックします。このキーワードが`true`の場合、エスケープアルゴリズムは**適用されず**、すべてのセル内にHTMLコードを許可します。この場合、ユーザーは出力コードが有効であることを確認する必要があります。少数のセルにHTMLコードがある場合は、[`HtmlCell`](@ref)オブジェクトでラップしてください。 (**デフォルト** = `false`)
  * `continuation_row_alignment::Symbol`：継続行のセルの整列を定義するシンボル。この行はテーブルが垂直に切り取られた場合に印刷されます。 (**デフォルト** = `:r`)
  * `highlighters::Union{HtmlHighlighter, Tuple}`：[`HtmlHighlighter`](@ref)のインスタンスまたはHTMLハイライターのリストを含むタプル（`HTML highlighters`セクションを参照）。
  * `linebreaks::Bool`：`true`の場合、`\n`は`<br>`に置き換えられます。 (**デフォルト** = `false`)
  * `maximum_columns_width::String`：各列の最大幅を持つ文字列。この文字列はHTMLで有効なサイズを含む必要があります。空でない場合、各セルには次のスタイルが適用されます：

      * `"max-width": <maximum_column_widthの値>`
      * `"overflow": "hidden"`
      * `"text-overflow": "ellipsis"`
      * `"white-space": "nowrap"`

    空の場合、追加のスタイルは適用されません。 (**デフォルト** = "")
  * `minify::Bool`：`true`の場合、出力は最小化され、すなわち不要なインデントや改行なしで表示されます。 (**デフォルト** = `false`)
  * `standalone::Bool`：`true`の場合、完全なHTMLページが生成されます。そうでない場合、`<table>`と`</table>`タグの間のコンテンツのみが印刷されます（タグを含む）。 (**デフォルト** = `false`)
  * `vcrop_mode::Symbol`：この変数は垂直切り取りの動作を定義します。`:bottom`の場合、必要に応じてデータは下部で切り取られます。一方、`:middle`の場合、必要に応じてデータは中央で切り取られます。 (**デフォルト** = `:bottom`)
  * `table_div_class::String`：テーブル`div`のクラス名。`wrap_table_in_div`が`true`の場合にのみ使用されます。 (**デフォルト** = "")
  * `table_class::String`：テーブルのクラス名。 (**デフォルト** = "")
  * `table_style::Dict{String, String}`：テーブル`style`に追加されるCSSプロパティとその値を含む辞書。 (**デフォルト** = `Dict{String, String}()`)
  * `tf::HtmlTableFormat`：HTMLテーブルの一般的な形式を定義する[`HtmlTableFormat`](@ref)のインスタンス。
  * `top_left_str::String`：上部バーの左位置に印刷される文字列。 (**デフォルト** = "")
  * `top_left_str_decoration::HtmlDecoration`：上部左文字列を印刷するために使用される装飾（`top_left_str`を参照）。 (**デフォルト** = `HtmlDecoration()`)
  * `top_right_str::String`：上部バーの右位置に印刷される文字列。この文字列は、省略されたセルの要約が表示される場合に置き換えられます。 (**デフォルト** = "")
  * `top_right_str_decoration::HtmlDecoration`：上部右文字列を印刷するために使用される装飾（`top_right_str`を参照）。 (**デフォルト** = `HtmlDecoration()`)
  * `wrap_table_in_div::Bool`：`true`の場合、テーブルは`div`でラップされます。 (**デフォルト**: `false`)

## HTMLハイライター

ハイライターのセットは、`highlighters`キーワードに`Tuple`として渡すことができます。各ハイライターは、[`HtmlHighlighter`](@ref)構造のインスタンスです。次の2つの公開フィールドを含みます：

  * `f::Function`：`f(data, i, j)`というシグネチャを持つ関数で、`data`内の要素`(i,j)`をハイライトする必要がある場合は`true`を返し、そうでない場合は`false`を返します。
  * `fd::Function`：`f(h, data, i, j)`というシグネチャを持つ関数で、`h`はハイライターです。この関数は、ハイライトする必要があるセルに適用される`HtmlDecoration`を返さなければなりません。

関数`f`は次のシグネチャを持ちます：

```
f(data, i, j)
```

ここで、`data`は印刷されているデータへの参照であり、`i`と`j`はテストされている要素の座標です。この関数が`true`を返すと、ハイライトスタイルが`(i, j)`要素に適用されます。そうでない場合、デフォルトスタイルが使用されます。

関数`f`が`true`を返すと、関数`fd(h, data, i, j)`が呼び出され、セルに適用される装飾を含む[`HtmlDecoration`](@ref)の要素を返さなければなりません。

HTMLハイライターは次の2つのヘルパーを使用して構築できます：

```
HtmlHighlighter(f::Function, decoration::HtmlDecoration)

HtmlHighlighter(f::Function, fd::Function)
```

最初のものは、ハイライトされたセルに`decoration`で指定された固定装飾を適用しますが、2番目のものは、ユーザーが関数`fd`を指定することで希望の装飾を選択できるようにします。

!!! info
    単一のハイライターが必要な場合は、`Tuple`内に入れずに`highlighter`キーワードに直接渡すことができます。


!!! note
    複数のハイライターが要素`(i, j)`に対して有効な場合、適用されるスタイルは、タプル`highlighters`内の順序を考慮して最初の一致と等しくなります。


!!! note
    ハイライターが[Formatters](@ref)と一緒に使用される場合、フォーマットの変更はハイライター関数`f`に渡されるパラメータ`data`に**影響しません**。常に元の未フォーマットの値が受け取られます。


---

# LaTeXバックエンド

このバックエンドはLaTeXテーブルを生成します。このバックエンドは`backend = Val(:latex)`を選択することで使用できます。

## キーワード

  * `body_hlines::Vector{Int}`：追加の水平線を描画する行番号を示す`Int`のベクター。1未満および印刷された行数以上の番号は無視されます。このベクターは`hlines`のものに追加されますが、ここでのインデックスはボディの印刷された行に関連しています。したがって、`1`が`body_hlines`に追加されると、最初のデータ行の後に水平線が描画されます。 (**デフォルト** = `Int[]`)
  * `highlighters::Union{LatexHighlighter, Tuple}`：`LatexHighlighter`のインスタンスまたはLaTeXハイライターのリストを含むタプル（`LaTeX highlighters`セクションを参照）。
  * `hlines::Union{Nothing, Symbol, AbstractVector}`：この変数は水平線が描画される場所を制御します。`nothing`、`:all`、`:none`または整数のベクターであることができます。 (**デフォルト** = `nothing`)

      * `nothing`の場合、デフォルトで、設定は変数`tf`のテーブル形式から取得されます（[`LatexTableFormat`](@ref)を参照）。
      * `:all`の場合、すべての水平線が描画されます。
      * `:none`の場合、水平線は描画されません。
      * 整数のベクターの場合、ベクター内の行の後にのみ水平線が描画されます。最上部の線は`0`が`hlines`に含まれている場合に描画され、ヘッダーとサブヘッダーは1行として考慮されます。さらに、この変数の行番号は**印刷された行**に関連していることを重要です。したがって、`show_header`オプションによってヘッダーを抑制する影響を受けます。最後に、便利のために、最上部と最下部の線はそれぞれこのベクターにシンボル`:begin`と`:end`を追加することで描画できます。

!!! info
    `body_hlines`の値はこのベクターに追加されます。したがって、`hlines`が`:none`であっても水平線を描画できます。


  * `label::AbstractString`：テーブルのラベル。空の場合、ラベルは追加されません。 (**デフォルト** = "")
  * `longtable_footer::Union{Nothing, AbstractString}`：ページ区切りの前にテーブルのフッターに描画される文字列。これは`table_type`が`:longtable`の場合にのみ機能します。`nothing`の場合、フッターは使用されません。 (**デフォルト** = `nothing`)
  * `row_number_alignment::Symbol`：行番号列の整列を選択します（`Alignment`セクションを参照）。 (**デフォルト** = `:r`)
  * `table_type::Union{Nothing, Symbol}`：テーブルを印刷するために使用されるLaTeX環境を選択します。現在サポートされているオプションは、`tabular`用の`:tabular`または`longtable`用の`:longtable`です。`nothing`の場合、テーブル形式のデフォルトオプションが使用されます。 (**デフォルト** = `nothing`)
  * `tf::LatexTableFormat`：LaTeXテーブルの一般的な形式を定義する[`LatexTableFormat`](@ref)のインスタンス。
  * `vlines::Union{Nothing, Symbol, AbstractVector}`：この変数は垂直線が描画される場所を制御します。`:all`、`:none`または整数のベクターであることができます。最初のケース（デフォルトの動作）では、すべての垂直線が描画されます。2番目のケースでは、垂直線は描画されません。3番目のケースでは、ベクター内の列の後にのみ垂直線が描画されます。左の境界は`0`が`vlines`に含まれている場合に描画されます。さらに、この変数の列番号は**印刷された列**に関連していることを重要です。したがって、`show_row_number`を使用して追加された列の影響を受けます。最後に、便利のために、左と右の境界はそれぞれこのベクターにシンボル`:begin`と`:end`を追加することで描画できます。 (**デフォルト** = `:none`)
  * `wrap_table::Union{Nothing, String}`：この変数は、テーブルを変数`wrap_table_environment`で定義された環境でラップするかどうかを制御します。デフォルトは`true`です。`false`の場合、印刷されたテーブルは`\begin{tabular}`で始まります。このオプションは`:longtable`では機能しません。`nothing`の場合、テーブル形式のデフォルトオプションが使用されます。 (**デフォルト** = `nothing`)

## LaTeXハイライター

ハイライターのセットは、`highlighters`キーワードに`Tuple`として渡すことができます。各ハイライターは、[`LatexHighlighter`](@ref)構造のインスタンスです。次の2つのフィールドを含みます：

  * `f::Function`：`f(data, i, j)`というシグネチャを持つ関数で、`data`内の要素`(i, j)`をハイライトする必要がある場合は`true`を返し、そうでない場合は`false`を返します。
  * `fd::Functions`：`f(data, i, j, str)::String`というシグネチャを持つ関数で、`data`は行列、`(i, j)`はテーブル内の要素の位置、`str`は文字列に変換されたデータです。この関数は、セルに配置される文字列を返さなければなりません。

関数`f`は次のシグネチャを持ちます：

```
f(data, i, j)
```

ここで、`data`は印刷されているデータへの参照であり、`i`と`j`はテストされている要素の座標です。この関数が`true`を返すと、ハイライトスタイルが`(i, j)`要素に適用されます。そうでない場合、デフォルトスタイルが使用されます。

関数`f`が`true`を返すと、関数`fd(data, i, j, str)`が呼び出され、セルに配置されるLaTeX文字列を返さなければなりません。

LaTeXハイライターを作成するために使用できる2つのヘルパーがあります：

```
LatexHighlighter(f::Function, envs::Union{String,Vector{String}})

LatexHighlighter(f::Function, fd::Function)
```

最初のものは、ハイライトされたテキストに`envs`内のすべてのLaTeX環境を再帰的に適用しますが、2番目のものは、ユーザーが関数`fd`を指定することで希望の装飾を選択できるようにします。

したがって、例えば：

```
LatexHighlighter((data, i, j) -> true, ["textbf", "small"])
```

は、テーブル内のすべてのセルを次の環境でラップします：

```
\textbf{\small{<Cell text>}}
```

!!! info
    単一のハイライターが必要な場合は、`Tuple`内に入れずに`highlighter`キーワードに直接渡すことができます。


!!! note
    複数のハイライターが要素`(i, j)`に対して有効な場合、適用されるスタイルは、タプル`highlighters`内の順序を考慮して最初の一致と等しくなります。


!!! note
    ハイライターが[Formatters](@ref)と一緒に使用される場合、フォーマットの変更はハイライター関数`f`に渡されるパラメータ`data`に**影響しません**。常に元の未フォーマットの値が受け取られます。


---

# Markdownバックエンド

このバックエンドはMarkdownテーブルを生成します。このバックエンドは`backend = Val(:markdown)`を選択することで使用できます。

## キーワード

  * `allow_markdown_in_cells::Bool`：デフォルトでは、`*`、`_`、`~`などの特殊なMarkdown文字は、Markdownバックエンドで有効な出力を生成するためにエスケープされます。ただし、このアルゴリズムはセル内でのMarkdownコードの使用をブロックします。このキーワードが`true`の場合、エスケープアルゴリズムは**適用されず**、すべてのセル内にMarkdownコードを許可します。この場合、ユーザーは出力コードが有効であることを確認する必要があります。 (**デフォルト** = `false`)
  * `highlighters::Union{MarkdownHighlighter, Tuple}`：`MarkdownHighlighter`のインスタンスまたはMarkdownハイライターのリストを含むタプル（`Markdown Highlighters`セクションを参照）。
  * `linebreaks::Bool`：`true`の場合、`\n`は`<br>`に置き換えられます。 (**デフォルト** = `false`)
  * `show_omitted_cell_summary::Bool`：`true`の場合、テーブルの後に省略された列と行の数を含む要約が印刷されます。 (**デフォルト** = `false`)

出力装飾をカスタマイズするために利用可能な次のキーワード：

  * `header_decoration::MarkdownDecoration`：ヘッダーに適用される装飾。 (**デフォルト** = `MarkdownDecoration(bold = true)`)
  * `row_label_decoration::MarkdownDecoration`：行ラベル列に適用される装飾。 (**デフォルト** = `MarkdownDecoration()`)
  * `row_number_decoration::MarkdownDecoration`：行番号列に適用される装飾。 (**デフォルト** = `MarkdownDecoration(bold = true)`)
  * `subheader_decoration::MarkdownDecoration`：サブヘッダーに適用される装飾。 (**デフォルト** = `MarkdownDecoration(code = true)`)

## Markdownハイライター

ハイライターのセットは、`highlighters`キーワードに`Tuple`として渡すことができます。各ハイライターは、[`MarkdownHighlighter`](@ref)構造のインスタンスです。次の2つの公開フィールドを含みます：

  * `f::Function`：`f(data, i, j)`というシグネチャを持つ関数で、`data`内の要素`(i,j)`をハイライトする必要がある場合は`true`を返し、そうでない場合は`false`を返します。
  * `fd::Function`：`fd(h, data, i, j)`というシグネチャを持つ関数で、`h`はハイライターです。この関数は、ハイライトする必要があるセルに適用される[`MarkdownDecoration`](@ref)を返さなければなりません。

関数`f`は次のシグネチャを持ちます：

```
f(data, i, j)
```

ここで、`data`は印刷されているデータへの参照であり、`i`と`j`はテストされている要素の座標です。この関数が`true`を返すと、ハイライトスタイルが`(i, j)`要素に適用されます。そうでない場合、デフォルトスタイルが使用されます。

関数`f`が`true`を返すと、関数`fd(h, data, i, j)`が呼び出され、セルに適用される[`MarkdownDecoration`](@ref)の要素を返さなければなりません。

Markdownハイライターは次の2つのヘルパーを使用して構築できます：

```
MarkdownHighlighter(f::Function, decoration::MarkdownDecoration)

MarkdownHighlighter(f::Function, fd::Function)
```

最初のものは、ハイライトされたセルに`decoration`で指定された固定装飾を適用しますが、2番目のものは、ユーザーが関数`fd`を指定することで希望の装飾を選択できるようにします。

!!! info
    単一のハイライターが必要な場合は、`Tuple`内に入れずに`highlighter`キーワードに直接渡すことができます。


!!! note
    複数のハイライターが要素`(i, j)`に対して有効な場合、適用されるスタイルは、タプル`highlighters`内の順序を考慮して最初の一致と等しくなります。


!!! note
    ハイライターが[Formatters](@ref)と一緒に使用される場合、フォーマットの変更はハイライター関数`f`に渡されるパラメータ`data`に**影響しません**。常に元の未フォーマットの値が受け取られます。


---

# フォーマッタ

キーワード`formatters`は、列内の値をフォーマットする関数を渡すために使用できます。これは、次のシグネチャを持つ関数のタプルでなければなりません：

```
f(v, i, j)
```

ここで、`v`はセル内の値、`i`は行番号、`j`は列番号です。したがって、これは値`v`を持つセル`(i, j)`のフォーマットされた値を返さなければなりません。返された値は、関数`sprint`を使用した後に文字列に変換されます。

このキーワードは単一の関数でも構いません。つまり、1つのフォーマッタのみが利用可能であることを意味します。また、`nothing`である場合は、フォーマッタは使用されません。

例えば、列2の奇数行のすべての値をπで乗算したい場合、フォーマッタは次のようになります：

```
formatters = (v, i, j) -> (j == 2 && isodd(i)) ? v * π : v
```

複数のフォーマッタが利用可能な場合、それらはタプル内にある順序で適用されます。したがって、次の`formatters`の場合：

```
formatters = (f1, f2, f3)
```

テーブル内の各要素`v`（i行目、j列目）は次のようにフォーマットされます：

```
v = f1(v,i,j)
v = f2(v,i,j)
v = f3(v,i,j)
```

したがって、ユーザーは呼び出し間で`v`の型が互換性があることを確認する必要があります。 ```
