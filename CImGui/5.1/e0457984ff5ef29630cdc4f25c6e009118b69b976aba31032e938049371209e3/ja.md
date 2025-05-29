```julia
SetNextFrameWantCaptureMouse(want_capture_mouse)

```

次のフレームで io.WantCaptureMouse フラグをオーバーライドします（このフラグはアプリケーションが処理するために残されており、通常は true の場合、アプリが入力を無視するよう指示します）。これは、次の NewFrame() 呼び出しの後に "io.WantCaptureMouse = want*capture*mouse;" を設定することと同等です。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1054).
