```julia
SetWindowFontScale(scale)

```

[OBSOLETE] フォントスケールを設定します。すべてのウィンドウをスケーリングしたい場合は、IO.FontGlobalScaleを調整してください。これは古いAPIです！正しいスケーリングのためには、フォントを再読み込みし、ImFontAtlasを再構築し、style.ScaleAllSizes()を呼び出すことをお勧めします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L431).
