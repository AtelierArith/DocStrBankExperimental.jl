```julia
TextUnformatted(text)
TextUnformatted(text, text_end)

```

Raw text without formatting. Roughly equivalent to Text("%s", text) but: A) doesn't require null terminated string if 'text_end' is specified, B) it's faster, no memory copy is done, no buffer size limits, recommended for long chunks of text.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L542).
