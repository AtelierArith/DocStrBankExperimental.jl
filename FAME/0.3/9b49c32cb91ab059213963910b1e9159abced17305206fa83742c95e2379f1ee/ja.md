```
readfame(db, args...; 
    namecase=lowercase,
    prefix=nothing, glue="_",
    collect=[], 
    wc_options...)
```

FAMEデータベースからJuliaにデータを読み込みます。データは[`Workspace`](@ref TimeSeriesEcon.Workspace)として返されます。

`db`は[`FameDatabase`](@ref)または`String`です。`db`が`String`の場合、データベースは`:readonly`モードで開かれ、データの読み込み後に閉じられます。

ファイルへのパスを含むdb文字列の場合、パスにスペースが含まれているときは、エスケープされた二重引用符で囲む必要があります。

`db`が唯一の引数である場合、データベース内のすべてのオブジェクトが読み込まれます。引数とオプションを使用して、どのオブジェクトが読み込まれるかを制限できます。

最初の引数の後の各位置引数は、文字列またはシンボルである必要があります。

  * ワイルドカード文字（`'?'`または`'^'`、ワイルドカードに関するFameヘルプを参照）を含む文字列の場合、[`listdb`](@ref)を呼び出して、指定されたワイルドカードに一致するオブジェクトのリストを取得します。この場合、指定された`wc_options...`を[`listdb`](@ref)に渡します。これらを使用して、特定のクラス、タイプ、頻度などにワイルドカード検索を制限できます。詳細については[`listdb`](@ref)を参照してください。
  * それ以外の場合（シンボルまたはワイルドカード文字を含まない文字列）、指定された名前のオブジェクトが読み込まれます。`wc_options...`は無視され、オブジェクトはそのクラス、タイプ、頻度に関係なく読み込まれます。

以下のオプションを使用して、FAME名からJulia識別子がどのように構築されるかを変更できます。

  * `namecase` - FAME識別子は大文字と小文字を区別せず、FAMEは常にそれらを大文字で返します。デフォルトでは、名前を小文字に変換します。`namecase`オプションの値として、文字列を受け取り文字列を返す任意の関数を渡すことができます。デフォルトは`lowercase`です。たとえば、データベースにJulia識別子で許可されていない記号を含む名前がある場合、これは良いアイデアかもしれません。現在、私たちは`Symbol(namecase(fo.name))`を呼び出していますが、そのような記号を他のものに置き換えたい場合があります。たとえば、`namecase=(x->lowercase(replace(x, "@"=>"_")))`のように。
  * `prefix`が指定されている場合、FAME名の先頭から（`glue`と一緒に）削除されます。名前が指定された`prefix`で始まらない場合、変更されません。指定されたプレフィックスで始まる名前のみを読み込みたい場合は、適切なワイルドカードを使用する必要があります。デフォルトは`prefix=nothing`で、この機能は無効になります。`prefix=nothing`と`prefix=""`は同じではないことに注意してください。
  * `collect`は文字列/シンボル、要素が文字列/シンボルまたは文字列/シンボルのベクトルなどであるベクトルである可能性があります。名前が指定された`collect`値のいずれか（`glue`と一緒に）で始まる場合、オブジェクトはネストされた[`Workspace`](@ref)に読み込まれます。アイデアは、データベースに書き込まれたネストされたWorkspacesが、`collect`オプション値にネストされたWorkspacesの名前のリストを提供することによって同じ構造で読み込まれることです。以下の例を参照してください。
  * `glue`は、`prefix`または`collect`文字列を名前の残りの部分に結合するために使用されます。これが機能するためには、[`writefame`](@ref)で使用されるのと同じ値を使用してください。

## 例

```
julia> w = Workspace(; a = 1, b=TSeries(2020Q1, randn(10)),
       s = MVTSeries(2020M1, (:q, :p), randn(24,2)),
       c = Workspace(; alpha = 0.1, beta = 0.8, 
       n = Workspace(; s = "Hello World")
       ))
Workspace with 4-variables
  a ⇒ 1
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  s ⇒ 24×2 MVTSeries{Monthly} with range 2020M1:2021M12 and variables (q,p)
  c ⇒ Workspace with 3-variables

julia> writefame("data.db", w); listdb("data.db")
7-element Vector{FameObject}:
 A: scalar,numeric,undefined,0:0,0:0
 B: series,precision,quarterly_december,2020:1,2022:2
 C_ALPHA: scalar,precision,undefined,0:0,0:0
 C_BETA: scalar,precision,undefined,0:0,0:0
 C_N_S: scalar,string,undefined,0:0,0:0
 S_P: series,precision,monthly,2020:1,2021:12
 S_Q: series,precision,monthly,2020:1,2021:12

julia> # リスト内の変数のみを読み込む
julia> readfame("data.db", "a", "b")
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2

julia> # データベースにあるようにすべてを読み込む
julia> readfame("data.db")
Workspace with 7-variables
        a ⇒ 1.0
        b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  c_alpha ⇒ 0.1
   c_beta ⇒ 0.8
    c_n_s ⇒ 11-codeunit String
      s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
      s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # プレフィックスが出現する場所で削除される（すべてを読み込む）
julia> readfame("data.db", prefix="c")
Workspace with 7-variables
      a ⇒ 1.0
      b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  alpha ⇒ 0.1
   beta ⇒ 0.8
    n_s ⇒ 11-codeunit String
    s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
    s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # ワイルドカード検索、プレフィックスなし（名前は変更されない）
julia> readfame("data.db", "s?")
Workspace with 2-variables
  s_p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
  s_q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # プレフィックス（削除）と一致するワイルドカード検索
julia> readfame("data.db", "s?", prefix="s")  
Workspace with 2-variables
  p ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12
  q ⇒ 24-element TSeries{Monthly} with range 2020M1:2021M12

julia> # 一致するワイルドカードを持つコレクト
julia> readfame("data.db", "c?", collect="c")   
Workspace with 1-variables
  c ⇒ Workspace with 3-variables

julia> # ネストされたコレクト - ネストされたWorkspacesの元の構造に一致
julia> readfame("data.db", collect=["c"=>["n"], "s"])  
Workspace with 4-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2
  c ⇒ Workspace with 3-variables
  s ⇒ Workspace with 2-variables

julia> readfame(""/home/usr/my data directory/data.db"", "a", "b")   
Workspace with 2-variables
  a ⇒ 1.0
  b ⇒ 10-element TSeries{Quarterly} with range 2020Q1:2022Q2

```
