```
speculate(predicate, value; parameters...)
speculate(value; parameters...)
```

コンパイル可能なメソッドを検索します。

参照: [`install_speculator`](@ref)。

!!! tip
    レイテンシを減らすために、パッケージ内でこれを使用してください。


!!! note
    これは、プリコンパイル中またはインタラクティブセッション中に呼び出されたとき、またはプリコンパイルディレクティブをファイルに書き込むときにのみ実行されます。


# パラメータ

  * `predicate = Returns(true)`:   これは、`predicate(::Module, ::Symbol)::Bool`というシグネチャを受け入れる必要があります。   `true`を返すと、`getproperty(::Module, ::Symbol)`を検索することを指定し、   `false`を返すと、値をスキップすることを指定します。   これは、与えられたモジュールと名前が`isdefined`および`!isdeprecated`を満たす場合に、   `Module`の名前を検索するときに呼び出され、メソッドパラメータから型を検索するときにも呼び出されます。   デフォルトの述語`Returns(true)`はすべての値を検索しますが、   述語`Returns(false)`はどの値も検索しません。   有用な述語には、`Base.isexported`、   `Base.ispublic`、および値自体のプロパティをチェックすることが含まれます。
  * `value`:   `Module`が与えられた場合、`speculate`はその内容を再帰的に検索し、   `names(::Module; all = true)`を使用して、非推奨でない、外部モジュールでない、   かつ`predicate`を満たす各定義された値を検索します。   他の値については、それぞれの一般的な`methods`が   対応するコンパイル可能なメソッドを検索します。

# キーワードパラメータ

  * `background::Bool = false`:   `:default`プールのスレッドで実行するかどうかを指定します。   利用可能なスレッドの数は、`Threads.nthreads(:default)`を使用して確認できます。
  * `dry::Bool = false`:   生成されたメソッドシグネチャに対して`precompile`を実行するかどうかを指定します。   これは、`verbosity = debug ∪ review`でテストするのに便利です。   特化されていることが知られているメソッドシグネチャはスキップされます。   `dry`は、`path`パラメータでディレクティブをファイルに保存するために`false`である必要があります。
  * `limit::Int = 1`:   一般的なメソッドから生成されるコンパイル可能なメソッドの最大数を指定します。   `1`未満の値はエラーをスローします。   それ以外の場合、各パラメータ型の直積からメソッドシグネチャが生成されます。   具体的な型と`@nospecialize`でマークされた型は直接使用されます。   それ以外の場合、具体的な型は`DataType`と`Union`のサブタイプから取得されます。   適切な値を設定することで、単一の一般的なメソッドのプリコンパイルに過度の時間を費やすのを防ぎます。
  * `path::String = ""`:   `path`が空でなく、`dry`実行でない場合、成功したプリコンパイルディレクティブをファイルに保存します。   コンパイルされたことが知られている生成されたメソッドはスキップされます。   結果のディレクティブは、実行するために追加のモジュールを読み込む必要がある場合があります。
  * `verbosity::Verbosity = warn`:   表示するログステートメントを指定します。   この関数がパッケージのプリコンパイルに使用される場合、   これは[`silent`](@ref)または[`warn`](@ref)に設定する必要があります。   参照: [`Verbosity`](@ref)。

# 例

```julia-repl
julia> module Showcase
           export g, h

           f() = nothing
           g(::Int) = nothing
           h(::Union{String, Symbol}) = nothing
       end;

julia> speculate(Showcase; verbosity = debug)
[ Info: Compiled `Main.Showcase.g(::Int)`
[ Info: Compiled `Main.Showcase.f()`

julia> speculate(Base.isexported, Showcase; verbosity = debug)
[ Info: Skipped `Main.Showcase.g(::Int)`

julia> speculate(Showcase.h; verbosity = debug) do m, n
           !(m == Core && n == :String)
       end
[ Info: Compiled `Main.Showcase.h(::Symbol)`

julia> speculate(Showcase.h; limit = 2, verbosity = debug)
[ Info: Skipped `Main.Showcase.h(::String)`
[ Info: Compiled `Main.Showcase.h(::Symbol)`
```
