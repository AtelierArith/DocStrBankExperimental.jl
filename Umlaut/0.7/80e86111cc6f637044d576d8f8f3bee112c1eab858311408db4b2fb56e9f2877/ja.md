```
trace(f, args...; ctx=BaseCtx())
```

関数呼び出しをトレースし、結果と対応するテープを返します。`trace`はテープにプリミティブメソッドを記録し、非プリミティブに再帰的に潜ります。

トレースはコンテキストと以下のメソッドを使用してカスタマイズできます：

  * isprimitive(ctx, f, args...) - `f(args...)`をプリミティブとして扱うべきかどうかを決定します。
  * record*primitive!(tape::Tape{C}, v*f, v*args...) - 変数`f*v(v_args...)`によって定義されたプリミティブ呼び出しをテープに記録します。

デフォルトのコンテキストは`BaseCtx()`で、標準のJuliaモジュールからのすべての関数をプリミティブとして扱い、単に呼び出しをテープにプッシュします。これらの関数のドキュメント文字列を参照して、カスタマイズのさらなる例を確認してください。

# 例：

```
foo(x) = 2x
bar(x) = foo(x) + 1

val, tape = trace(bar, 2.0)
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = *(2, %2)::Float64
#   %4 = +(%3, 1)::Float64
# )

val, tape = trace(bar, 2.0; ctx=BaseCtx([*, +, foo]))
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = foo(%2)::Float64
#   %4 = +(%3, 1)::Float64
# )

struct MyCtx end

isprimitive(ctx::MyCtx, f, args...) = isprimitive(BaseCtx(), f, args...) || f in [foo]
val, tape = trace(bar, 2.0; ctx=MyCtx())
# (5.0, Tape{Dict{Any, Any}}
#   inp %1::typeof(bar)
#   inp %2::Float64
#   %3 = foo(%2)::Float64
#   %4 = +(%3, 1)::Float64
# )
```
