# ExceptionUnwrapping.jl

`ExceptionUnwrapping.jl`は、"ラップされた例外"を検査し、アンラップするための例外処理ユーティリティを提供します。ここで言う"ラップされた例外"とは、別の例外を埋め込んでいる任意の例外タイプを指します。

最も一般的な例は`TaskFailedException`で、これは`Task`とその`Task`が失敗する原因となった例外をラップします。別の例としては、[Salsa.jl](https://github.com/RelationalAI-oss/Salsa.jl)の例外タイプがあります。

## API

  * `has_wrapped_exception(e, ExceptionType)::Bool`
  * `is_wrapped_exception(e)::Bool`
  * `unwrap_exception(exception_wrapper) -> wrapped_exception`
  * `unwrap_exception(normal_exception) -> normal_exception`
  * `unwrap_exception_until(e, ExceptionType)::ExceptionType`
  * `unwrap_exception_to_root(exception_wrapper) -> wrapped_exception`
  * `unwrap_exception_to_root(normal_exception) -> normal_exception`

## 使用法

ライブラリがラップされた例外タイプを提供する場合は、`unwrap_exception`にメソッドを追加することで、このパッケージに登録する必要があります：

```julia
ExceptionUnwrapping.unwrap_exception(e::MyWrappedException) = e.exception
```

クライアントコードでは、catchブロック内で`has_wrapped_exception`と`unwrap_exception_until`を使用するべきです：

```julia
try
    ...
catch e
    if has_wrapped_exception(e, BoundsError)
        be = unwrap_exception_until(e, BoundsError)
        # ...BoundsErrorを使用...
    else
        rethrow()
    end
end
```

最後に、`@test_throws_wrapped`を使用してクライアントテストの堅牢性を向上させることができます：

```julia
@test_throws_wrapped AssertionError my_possibly_multithreaded_function()
```

## 動機付けの例: 安定した例外処理

### 問題: ライブラリに並行性を追加すると、ユーザーの例外処理が壊れる可能性がある

私たちが並行性をより多く使用し始めると、例外処理が少し奇妙になることがあります。Juliaの協調マルチスレッドは、基本的な原則として*合成可能*であるように設計されていますが、同期コードを`Task`で並行して実行するように変更すると、**そのコードがスローする例外のタイプが変わります！**

例えば、特定のタイプの例外（`BoundsError`）を処理して意味のあるアクション（ユーザーに再試行を促す）を取ることを望むこの愚かなプログラムを考えてみてください：

```julia
function get_and_sort_names_by_first_letter(n)
    try
        names = [readline() for _ in 1:n]
        # このライブラリのソート関数を使用するのは、すごく速いはずだから🤘
        return library_sort(names, by=a->a[1])
    catch e
        if e isa BoundsError
            println("おっと！空の名前を入力しました。もう一度試してください！")
            # ユーザーにもう一度チャンスを与える
            return get_and_sort_names_by_first_letter(n)
        else
            rethrow()  # 不明なエラー
        end
    end
end
```

すべてはうまくいっています：

```julia
julia> get_and_sort_names_by_first_letter(2)

Valentin
おっと！空の名前を入力しました。もう一度試してください！
Valentin
Jane
2-element Array{String,1}:
 "Jane"
 "Valentin"
```

しかし、そのライブラリが*ソート関数を並列化*することに決めた場合、今ではさらに速くなります（🤘🤘）？

```julia
# 笑、まあ、これでは速くはならないが、ポイントを示しています。
library_sort(args...; kwargs...) = fetch(Threads.@spawn sort(args...; kwargs...))
```

*何が起こるか*というと、ライブラリは意図せずに呼び出し元を壊してしまいます：

```julia
julia> get_and_sort_names_by_first_letter(2)

Nathan
ERROR: TaskFailedException:
BoundsError: attempt to access String
  at index [1]
Stacktrace:
 [1] checkbounds at ./strings/basic.jl:193 [inlined]
 [2] codeunit at ./strings/string.jl:89 [inlined]
 [3] getindex at ./strings/string.jl:210 [inlined]
 [4] #10 at /Users/nathan.daly/.julia/dev/ExceptionUnwrapping/src/ExceptionUnwrapping.jl:125 [inlined]
 [5] lt(::Base.Order.By{var"#10#12"}, ::String, ::String) at ./ordering.jl:51
 [6] sort!(::Array{String,1}, ::Int64, ::Int64, ::Base.Sort.InsertionSortAlg, ::Base.Order.By{var"#10#12"}) at ./sort.jl:468
 [7] sort!(::Array{String,1}, ::Int64, ::Int64, ::Base.Sort.MergeSortAlg, ::Base.Order.By{var"#10#12"}, ::Array{String,1}) at .
```

ライブラリは`BoundsError`を返すことを約束していないため、遭遇した`TaskFailedException`を処理してアンラップする必要があることを知ることはできません。ユーザーは*TaskFailedExceptionを見たい*と思うかもしれません。そして、ユーザーのコードは、提供したラムダから直接来ているため、`BoundsError`に依存することに安心感を持っていたので、どのような例外が生成されるかを知っていると思っていました。

そして、このコードパスは*エラーハンドリング*であるため、十分にテストされていない可能性があります！

なんという難題でしょう！そこで、私たちはここに解決策を提示します：`ExceptionUnwrapping.jl`

### 解決策: ExceptionUnwrapping.jl

ユーザーが常に例外チェックを`ExceptionUnwrapping`を使用して構造化すれば、基盤となる並行モデルに変更があっても、引き続き機能します：

```julia
function get_and_sort_names_by_first_letter(n)
    try
        names = [readline() for _ in 1:n]
        # このライブラリのソート関数を使用するのは、すごく速いはずだから🤘
        return library_sort(names, by=a->a[1])
    catch e
      # ExceptionUnwrappingのチェックを使用して、`e`がBoundsErrorであるか、
      # BoundsErrorをラップしているかを確認します。
      if has_wrapped_exception(e, BoundsError)
            println("おっと！空の名前を入力しました。もう一度試してください！")
            # ユーザーにもう一度チャンスを与える
            return get_and_sort_names_by_first_letter(n)
        else
            rethrow()  # 不明なエラー
        end
    end
end
```

これで、`library_sort`が内部でタスクを使用しているかどうかに関係なく、再び機能するようになります。これが、合成可能なマルチスレッドから私たちが望むことです！ :)

```julia
julia> get_and_sort_names_by_first_letter(2)

Nathan
おっと！空の名前を入力しました。もう一度試してください！
Nathan
Martin
2-element Array{String,1}:
 "Martin"
 "Nathan"
```

---

## 用語:

### "ラップされた例外" vs "例外の原因"

Juliaでは、ある例外は別の例外によって"引き起こされる"ことがあります。これは、`catch`ブロック（または`finally`ブロック）内で新しい例外がスローされる場合です。これは*このパッケージが対処している状況ではありません*。

例えば：

```julia
julia> try
           throw(ErrorException("1"))
       catch e
           throw(ErrorException("2"))
       end
ERROR: 2
Stacktrace:
 [1] top-level scope at REPL[1]:4
caused by [exception 1]
1
Stacktrace:
 [1] top-level scope at REPL[1]:2
```

これは、Juliaの標準ライブラリによってすでに十分にカバーされている状況であり、`Base.catch_stack()`のような関数が、スローされた例外のスタックを返します（上記の`caused by`表示を印刷するために使用されます）。

代わりに、このパッケージは、情報やコンテキストを追加するため、または例外メカニズムがタスク間の境界を越えられないために、別の例外を内部に埋め込んでいる例外を指す*「ラップされた例外」*を扱うためのものです。
