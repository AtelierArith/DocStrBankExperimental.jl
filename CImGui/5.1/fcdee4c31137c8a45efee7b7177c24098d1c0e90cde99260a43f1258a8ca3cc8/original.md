```julia
EndFrame()

```

Ends the Dear ImGui frame. automatically called by Render(). If you don't need to render data (skipping rendering) you may call EndFrame() without Render()... but you'll have wasted CPU already! If you don't need to render, better to not create any windows and not call NewFrame() at all!

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L344).
