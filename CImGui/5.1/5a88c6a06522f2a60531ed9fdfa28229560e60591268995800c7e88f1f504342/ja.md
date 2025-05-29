```julia
DestroyPlatformWindows()

```

すべてのビューポートのためにDestroyWindowプラットフォーム関数を呼び出します。imguiのシャットダウンの前にプラットフォームウィンドウを閉じる必要がある場合は、バックエンドのShutdown()から呼び出してください。そうでなければ、DestroyContext()によって呼び出されます。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1095).
