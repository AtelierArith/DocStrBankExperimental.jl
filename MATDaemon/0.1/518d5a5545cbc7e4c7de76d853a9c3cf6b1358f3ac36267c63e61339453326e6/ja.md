# MATDaemon.jl

*"はい、もちろんダクトテープは真空に近い状態でも機能します。ダクトテープはどこでも機能します。ダクトテープは魔法であり、崇拝されるべきです。" ― アンディ・ウィアー, 『火星の人』*

[![dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://jondeuce.github.io/MATDaemon.jl/dev) [![build status](https://github.com/jondeuce/MATDaemon.jl/workflows/CI/badge.svg)](https://github.com/jondeuce/MATDaemon.jl/actions?query=workflow%3ACI) [![codecov.io](https://codecov.io/github/jondeuce/MATDaemon.jl/branch/master/graph/badge.svg)](http://codecov.io/github/jondeuce/MATDaemon.jl/branch/master)

[`DaemonMode.jl`](https://github.com/dmolina/DaemonMode.jl)によって起動されたJuliaデーモンを使用して、MATLABからJuliaを呼び出します。

## クイックスタート

MATLAB関数[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)を使用して、MATLABからJuliaを呼び出します：

```matlab
>> jlcall('sort', {rand(2,5)}, struct('dims', int64(2)))

ans =

    0.1270    0.2785    0.6324    0.8147    0.9575
    0.0975    0.5469    0.9058    0.9134    0.9649
```

[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)に渡される位置引数は次のとおりです：

1. 呼び出すJulia関数をMATLABの`char`配列として指定します。これは、関数に評価される任意のJulia式であることができます。例えば、`'a=2; b=3; x -> a*x+b'`。便利のために、空の文字列`''`は`'(args...; kwargs...) -> nothing'`として解釈され、任意の入力に対して`nothing`を返します。**注意：**式は`let`ブロック内にラップされ、グローバルスコープで評価されます。
2. 位置引数はMATLABの`cell`配列として指定されます。例えば、`args = {arg1, arg2, ...}`
3. キーワード引数はMATLABの`struct`として指定されます。例えば、`kwargs = struct('key1', value1, 'key2', value2, ...)`

[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)が最初に呼び出されると：

1. `MATDaemon.jl`がローカルのJuliaプロジェクトにインストールされます。プロジェクトが存在しない場合。デフォルトでは、`jlcall.m`と同じフォルダに`.jlcall`というフォルダが作成されます。
2. Juliaサーバーがバックグラウンドで[`DaemonMode.jl`](https://github.com/dmolina/DaemonMode.jl)を使用して起動されます。

以降のすべてのJuliaへの呼び出しはJuliaサーバーで実行されます。MATLABが終了すると、サーバーは自動的に終了します。

### Juliaサーバーの再起動

Juliaサーバーが望ましくない状態に達した場合、`'restart'`フラグに`true`の値を渡すことでサーバーを再起動できます：

```matlab
>> jlcall('', 'restart', true) % Juliaサーバーを再起動し、何も返さない
```

同様に、再起動せずにJuliaサーバーをシャットダウンすることもできます：

```matlab
>> jlcall('', 'shutdown', true) % Juliaサーバーをシャットダウンし、何も返さない
```

### Julia環境の設定

Julia関数を呼び出す前に、最初にJulia環境を設定する必要がある場合や便利な場合があります。例えば、ローカルの[プロジェクト環境](https://github.com/jondeuce/MATDaemon.jl#loading-code-from-a-local-project)をアクティブにしたり、[セットアップスクリプト](https://github.com/jondeuce/MATDaemon.jl#loading-setup-code)を実行したり、後で使用するために[モジュール](https://github.com/jondeuce/MATDaemon.jl#loading-setup-code)をインポートしたり、マルチスレッドコードを実行するための[スレッド数](https://github.com/jondeuce/MATDaemon.jl#julia-multithreading)を設定したりすることができます。

このセットアップは、次のように[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)への単一の呼び出しでMATLABスクリプトの開始時に便利に実行できます：

```matlab
>> jlcall('', ...
    'project', '/path/to/MyProject', ... % ローカルJuliaプロジェクトをアクティブにする
    'setup', '/path/to/setup.jl', ... % カスタムJuliaコードをロードするためのセットアップスクリプトを実行する
    'modules', {'MyProject', 'LinearAlgebra', 'Statistics'}, ... % カスタムモジュールとBase Juliaのいくつかのモジュールをロードする
    'threads', 'auto', ... % デフォルトのJuliaスレッド数を使用する
    'restart', true ... % 新しいJuliaサーバー環境を開始する
    )
```

これらのフラグに関する詳細は、以下の対応するセクションを参照してください。

### Juliaマルチスレッド

Juliaサーバーで使用されるスレッド数は、`'threads'`フラグを使用して設定できます：

```matlab
>> jlcall('() -> Threads.nthreads()', 'threads', 8, 'restart', true)

ans =

  int64

   8
```

`'threads'`のデフォルト値は`'auto'`で、Juliaがスレッド数を選択します。

**注意：** Juliaは実行時にスレッド数を変更できません。`'threads'`フラグを有効にするには、サーバーを再起動する必要があります。

### モジュールの読み込み

Juliaモジュールを読み込んで使用できます：

```matlab
>> jlcall('LinearAlgebra.norm', {[3.0; 4.0]}, 'modules', {'LinearAlgebra'})

ans =

     5
```

**注意：** モジュールは`import`を使用して読み込まれ、`using`ではありません。したがって、モジュールシンボルは完全に修飾される必要があります。上記の例では`LinearAlgebra.norm`のように、`norm`ではありません。

### 永続的な環境

デフォルトでは、以前に読み込まれたJuliaコードは、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)への後続の呼び出しで利用可能です。例えば、`LinearAlgebra.norm`への[上記の呼び出し](https://github.com/jondeuce/MATDaemon.jl#loading-modules)の後、`LinearAlgebra`を再度読み込むことなく`LinearAlgebra.det`関数を呼び出すことができます：

```matlab
>> jlcall('LinearAlgebra.det', {[1.0 2.0; 3.0 4.0]})

ans =

    -2
```

### ユニークな環境

`'shared'`フラグを`false`に設定することで、各Julia呼び出しをJuliaサーバーの別の名前空間で評価できます：

```matlab
% 'shared'をfalseに設定してサーバーを再起動
>> jlcall('LinearAlgebra.norm', {[3.0; 4.0]}, 'modules', {'LinearAlgebra'}, 'restart', true, 'shared', false)

ans =

     5

% この呼び出しはエラーになります。上記のコマンドがLinearAlgebraモジュールを読み込んでいるにもかかわらず、LinearAlgebra.normは新しい名前空間で評価されるためです。
>> jlcall('LinearAlgebra.norm', {[3.0; 4.0]}, 'shared', false)
ERROR: LoadError: UndefVarError: LinearAlgebra not defined
Stacktrace:
 ...
```

### ユニークなJuliaインスタンス

持続的なJuliaサーバーでJuliaコードを実行する代わりに、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)への各呼び出しに対してユニークなJuliaインスタンスを起動することができます。これは、`'server'`フラグに`false`の値を渡すことで実現されます。

**注意：** これは、Juliaパッケージの事前コンパイルと読み込みのため、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)を繰り返し呼び出す際にかなりのオーバーヘッドを引き起こす可能性があります：

```matlab
>> tic; jlcall('x -> sum(abs2, x)', {1:5}, 'server', false); toc
Elapsed time is 4.181178 seconds. % ユニークなJuliaインスタンスを呼び出す

>> tic; jlcall('x -> sum(abs2, x)', {1:5}, 'restart', true); toc
Elapsed time is 5.046929 seconds. % Juliaサーバーを再初期化

>> tic; jlcall('x -> sum(abs2, x)', {1:5}); toc
Elapsed time is 0.267088 seconds. % サーバーを呼び出す; かなり速い
```

### ローカルプロジェクトからのコードの読み込み

[ローカルJuliaプロジェクト](https://pkgdocs.julialang.org/v1/environments/)からコードを読み込んで呼び出すことができます：

```matlab
>> jlcall('MyProject.my_function', args, kwargs, ...
    'project', '/path/to/MyProject', ...
    'modules', {'MyProject'})
```

**注意：** `'project'`フラグを介して渡される文字列は、単に`Pkg.activate`に転送されます。プロジェクトの依存関係がインストールされていることを確認するのはユーザーの責任です。

### セットアップコードの読み込み

Julia関数は、MATLABから直接渡すことができない、またはMATLABに読み込むことができない型を必要とする場合があります。例えば、`Base.VERSION`をクエリしたいとします。単純に`jlcall('() -> Base.VERSION')`を呼び出すと失敗します。なぜなら、`typeof(Base.VERSION)`は`String`ではなく`VersionNumber`だからです。

1つの解決策は、Juliaスクリプト内にラッパー関数を定義することです：

```julia
# setup.jl
julia_version() = string(Base.VERSION)
```

次に、`'setup'`フラグを使用して上記のスクリプトを[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)に渡します：

```matlab
>> jlcall('julia_version', 'setup', '/path/to/setup.jl')

ans =

    '1.6.1'
```

この場合、`jlcall('() -> string(Base.VERSION)')`も同様に機能します。しかし一般的に、MATLAB型を使用して複雑なJuliaライブラリとインターフェースすることは簡単ではなく、`'setup'`フラグは任意のセットアップコードを実行することを可能にします。

**注意：** セットアップスクリプトは`include`を使用してグローバルスコープに読み込まれます。[永続的な環境](https://github.com/jondeuce/MATDaemon.jl#persistent-environments)を使用する場合、セットアップスクリプトで定義されたシンボルは、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)への後続の呼び出しで利用可能になります。

### Julia出力の処理

Juliaからの出力は、MATLABの`cell`配列[`varargout`](https://www.mathworks.com/help/matlab/ref/varargout.html)を使用して返されます。MATLAB互換の値にJulia値を変換するために、ヘルパー関数`MATDaemon.matlabify`が使用されます。具体的には、次のルールが使用されて`varargout`にJulia出力`y`を格納します：

1. `y::Nothing`の場合、`varargout = {}`となり、MATLABに出力は返されません。
2. `y::Tuple`の場合、`length(y)`の出力が返され、`varargout{i}`は`matlabify(y[i])`によって与えられます。
3. それ以外の場合、1つの出力が返され、`varargout{1}`は`matlabify(y)`によって与えられます。

デフォルトで定義されている`matlabify`メソッドは次のとおりです：

```julia
matlabify(x) = x # デフォルトのフォールバック
matlabify(::Union{Nothing, Missing}) = zeros(0,0) # MATLABの[]に相当
matlabify(x::Symbol) = string(x)
matlabify(xs::Tuple) = Any[matlabify(x) for x in xs] # matlabify値
matlabify(xs::Union{<:AbstractDict, <:NamedTuple, <:Base.Iterators.Pairs}) = Dict{String, Any}(string(k) => matlabify(v) for (k, v) in pairs(xs)) # キーを文字列に変換し、値をmatlabify
```

**注意：** MATLABの`cell`および`struct`型は、Juliaの`Array{Any}`および`Dict{String, Any}`に対応します。

`matlabify`を介した変換は、追加の型に簡単に拡張できます。[上記のセクション](https://github.com/jondeuce/MATDaemon.jl#loading-setup-code)の例に戻ると、`Base.VersionNumber`のための`matlabify`メソッドを定義できます：

```julia
# setup.jl
MATDaemon.matlabify(v::Base.VersionNumber) = string(v)
```

これで、戻り値の型は自動的に変換されます：

```matlab
>> jlcall('() -> Base.VERSION', 'setup', '/path/to/setup.jl')

ans =

    '1.6.1'
```

### トラブルシューティング

Juliaサーバーが不具合の状態に陥った場合、以下のトラブルシューティングのヒントが役立つかもしれません：

  * サーバーを再起動してみてください：`jlcall('', 'restart', true)`
  * 詳細なログのためにデバッグモードを有効にします：`jlcall('', 'debug', true)`
  * サーバーを呼び出すのではなく、Juliaを直接呼び出します：`jlcall('', 'server', false)`

      * これは遅くなります。なぜなら、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)への各呼び出しが新しいJuliaインスタンスを開始するためですが、[Windowsのサーバーの問題を修正するかもしれません](https://github.com/jondeuce/MATDaemon.jl/issues/9#issuecomment-1761710048)。
  * `MATDaemon.jl`のJuliaプロジェクト環境を更新します（注意：これによりサーバーが再起動します）：`jlcall('', 'update', true)`
  * `MATDaemon.jl`のワークスペースフォルダを再インストールします（注意：これによりサーバーが再起動します）：`jlcall('', 'reinstall', true)`

      * デフォルトでは、ワークスペースフォルダは`.jlcall`という名前で、[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)と同じディレクトリに保存されます。
      * `'reinstall'`フラグはワークスペースフォルダを削除し、`MATDaemon.jl`を再インストールさせます。手動で削除することもできます。

### パフォーマンス

MATLABの入力とJuliaの出力は、一時的な`.mat`ファイルに書き込むことによってMATLABと`DaemonMode.jl`サーバーの間で行き来します。これらのファイルの場所は、それぞれ`'infile'`および`'outfile'`フラグで構成できます。可能な場合は、これらのファイルをRAMバックのファイルシステムに指し示すことをお勧めします（例えば、Linuxの`/tmp`フォルダは通常RAMバックです）。読み取り/書き込み速度が向上する可能性があります。これは現在のデフォルトです；`'infile'`および`'outfile'`はMATLABの`tempname`関数を介して作成されます（このヒントを提供してくれた@mauro3に感謝します）。

それにもかかわらず、これはJuliaを呼び出す際にいくつかのオーバーヘッドを引き起こします。特にMATLABの入力やJuliaの出力が大きなメモリフットプリントを持つ場合はそうです。したがって、パフォーマンスが重要なループで[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)を使用することはお勧めできません。

## MATLABとJuliaのバージョン互換性

このパッケージはさまざまなMATLABバージョンでテストされています。ただし、一部のJuliaおよびMATLABのバージョンでは、外部ライブラリのサポートバージョンが衝突する可能性があります。例えば、Julia v1.6.1とMATLAB R2015bを使用して[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)を実行すると、次のエラーが発生します：

```matlab
>> jlcall

ERROR: Unable to load dependent library ~/.local/julia-1.6.1/bin/../lib/julia/libjulia-internal.so.1

Message: /usr/local/MATLAB/R2015b/sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.20' not found (required by ~/.local/julia-1.6.1/bin/../lib/julia/libjulia-internal.so.1)
```

このエラーは、サポートされている`libstdc++`バージョンの衝突によって発生し、Julia v1.5.4とMATLAB R2015b、またはJulia v1.6.1とMATLAB R2020bを使用している場合には発生しません。

この問題が発生した場合は、[`Julia`](https://github.com/JuliaLang/julia/blob/master/doc/build/build.md#required-build-tools-and-external-libraries)および[`MATLAB`](https://www.mathworks.com/support/requirements/supported-compilers.html)のドキュメントを参照して、相互にサポートされている外部ライブラリに関する情報を確認してください。

## このパッケージについて

このリポジトリには、Juliaコードを解析して実行し、MATLAB引数をJuliaに渡し、MATLABからJulia出力を取得するためのユーティリティが含まれています。

`MATDaemon.jl`と[`jlcall.m`](https://github.com/jondeuce/MATDaemon.jl/blob/v0.1.4/api/jlcall.m)の背後にある作業馬は、バックグラウンドで持続的なJuliaサーバーを起動するために使用される[`DaemonMode.jl`](https://github.com/dmolina/DaemonMode.jl)です。
