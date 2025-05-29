```
compile_traces(mod::Module, trace_files::AbstractString...; verbose=false, progress=true, warn=false, inline=false)
compile_traces(mod::Module, trace_files::AbstractVector{<:AbstractString}; verbose=false, progress=true, warn=false, inline=false)
```

1つ以上のトレースファイルからプリコンパイルステートメントのセットを実行し、`CompilationMetrics`結果を返します。

トレースファイルのパスは、Windowsでは'/'を'\'に置き換えて、OSにおおよそ正規化されます。

`verbose = false`は`progress = false`を意味します。`progress = false`をオフにするのは、`\r`が十分にサポートされていない場合、つまりCIでのことです。

`warn = true`は、特定のステートメントのプリコンパイルに失敗した場合に警告を発します。

特定のオプションは環境変数によって上書きされる場合があります。これらの変数は`JULIA_COMPILE_TRACES_<OPTION>`の形式であり、`JULIA_DEBUG`と同様に動作します：これらの変数の値はカンマ区切りのモジュールのリストであり、リストに表示されるモジュールに対して対応するオプションが有効になります。利用可能なオプションは次のとおりです：

  * `JULIA_COMPILE_TRACES_VERBOSE`: 指定されたモジュールに対して`verbose`ブールパラメータの値を`true`に設定します。
  * `JULIA_COMPILE_TRACES_WARN`: 指定されたモジュールに対して`warn`ブールパラメータの値を`true`に設定します。

例えば、`JULIA_COMPILE_TRACES_WARN=PackageA,PackageB`は、`mod::Module`引数が`PackageA`または`PackageB`のいずれかの名前を持つ場合に、パラメータ`warn`を強制的に`true`に設定します。

`inline`がtrueに設定されている場合、`precompile(...)`ディレクティブは`mod`内で実行されます。そうでない場合、特別な名前空間を持つ新しいモジュールが`mod`内に作成され、Juliaセッションで読み込まれた任意のモジュールを参照することができます。`inline`に使用する値は、トレースファイルの形式によって異なります。これは、生成方法に応じて2つの形式のいずれかになります：

  * コマンドラインオプション`--trace-file=<file>`によって生成されたトレースファイル：これには`inline = false`の使用が必要です。すべての関数とほとんどの型は、その定義モジュールで接頭辞が付けられます。例えば、`Base.collect`、`Base.getindex`など、コードが評価されたスコープに関係なくです。
  * [SnoopCompile.jl](https://github.com/timholy/SnoopCompile.jl)によって`SnoopCompile.parcel`を使用して生成されたトレースファイル：これには`inline = true`の使用が必要です。すべての関数と型は、トレースが生成されたパッケージのスコープにあると仮定されます。

2つの形式の違いは、後でプリコンパイルディレクティブを実行する際に使用されると仮定されるスコープです。すべてのトレースファイルは*同じ形式でなければなりません*が、異なる形式のトレースファイルを使用する2回の`compile_traces`呼び出しを行うことができます。

!!! warning
    トレースがパッケージのプリコンパイル中にコンパイルされることを意図している場合、`mod` **は**プリコンパイルされるモジュールでなければなりません（つまり、`@__MODULE__`）。そうでない場合、次のような悪名高いエラーが発生します：

    > ERROR: LoadError: 閉じられたモジュール<mod>への評価は、サイドエフェクトが永続的でないため、インクリメンタルコンパイルを壊します。これは、プリコンパイル中に`eval`で<mod>を変更する他のモジュールがあるためです - これを行わないでください。


既知のモジュールと型にバインドされているステートメントのみがコンパイルされます。ただし、`--trace-file=<file>`からプリコンパイルステートメントを使用する場合、セッションにトップレベルのパッケージまたはモジュールがロードされているだけで十分です。パッケージAがBの型を使用している場合、BはすでにAと共にロードされており、セッションに知られていることになります。

`Main`で定義された型や関数を含むスクリプトからトレースファイルを生成する場合、`Main.`を含むトレースをフィルタリングすることが良いプラクティスかもしれません。そうでないと、実行中のセッションで定義された関数や型を本当にコンパイルしている場合を除き、警告が発生します。 ```
