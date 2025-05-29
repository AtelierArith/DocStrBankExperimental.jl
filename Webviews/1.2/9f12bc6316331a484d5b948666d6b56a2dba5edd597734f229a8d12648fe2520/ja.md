```
Webview(
    size=(1024, 768);
    title="",
    debug=false,
    size_fixed=false,
    unsafe_window_handle=C_NULL,
    enable_webio=true,
    auto_terminate=true
)
Webview(width, height; kwargs...)
```

`size` と `title` を指定して新しい webview インスタンスを作成します。

  * `debug` が true の場合、開発者ツールが有効になります（プラットフォームがそれをサポートしている場合）。
  * **UNSAFE** `unsafe_window_handle` は、プラットフォーム固有のネイティブウィンドウハンドルへの危険なポインタである可能性があります。

非 null の場合、子 WebView は指定された親ウィンドウに埋め込まれます。そうでない場合は、新しいウィンドウが作成されます。プラットフォームに応じて、`GtkWindow`、`NSWindow`、または `HWND` ポインタをここに渡すことができます。

  * `enable_webio` が true の場合、WebIO が有効になります。
  * `auto_terminate=true` のすべての webview が破棄されると、プロセスは終了します。
