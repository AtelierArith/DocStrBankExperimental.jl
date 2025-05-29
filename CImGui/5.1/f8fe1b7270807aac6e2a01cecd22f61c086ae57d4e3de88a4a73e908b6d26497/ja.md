```julia
UpdatePlatformWindows()

```

メインループで呼び出します。各セカンダリビューポートに対してCreateWindow/ResizeWindow/etc.プラットフォーム関数を呼び出し、非アクティブなビューポートに対してDestroyWindowを呼び出します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1093).
