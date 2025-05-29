```julia
RenderPlatformWindowsDefault()
RenderPlatformWindowsDefault(platform_render_arg)
RenderPlatformWindowsDefault(
    platform_render_arg,
    renderer_render_arg
)

```

メインループで呼び出します。ImGuiViewportFlags_Minimizedフラグが設定されていない各セカンダリビューポートに対して、RenderWindow/SwapBuffersプラットフォーム関数を呼び出します。カスタムレンダリングのニーズに応じてユーザーによって再実装される可能性があります。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1094).
