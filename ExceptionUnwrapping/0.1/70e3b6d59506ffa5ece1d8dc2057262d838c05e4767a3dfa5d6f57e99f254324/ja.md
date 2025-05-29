```
summarize_current_exceptions(
    io::IO = Base.stderr,
    task = current_task(),
    show_fn = Base.showerror,
)
```

現在のタスクの例外の要約を `io` に印刷します。 `show_fn` として `Base.showerror` のカスタム実装を渡すことができます。

これは、例外スタックが大きい場合や、バックトレースが大きい場合、複数の部分を持つ CompositeExceptions が関与している場合に特に役立ちます。例外の要約のフォーマットや内容を制御するために、`Base.showerror` のカスタム実装を使用できます。
