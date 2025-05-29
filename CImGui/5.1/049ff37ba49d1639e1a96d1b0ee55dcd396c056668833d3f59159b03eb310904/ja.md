```julia
SetNextFrameWantCaptureKeyboard(want_capture_keyboard)

```

次のフレームで io.WantCaptureKeyboard フラグをオーバーライドします（このフラグはアプリケーションが処理するために残されており、通常は true の場合、アプリが入力を無視するよう指示します）。例えば、ウィジェットがホバーされているときにキーボードのキャプチャを強制することができます。これは「io.WantCaptureKeyboard = want*capture*keyboard」を設定することと同等です；次の NewFrame() 呼び出しの後に行います。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1006).
