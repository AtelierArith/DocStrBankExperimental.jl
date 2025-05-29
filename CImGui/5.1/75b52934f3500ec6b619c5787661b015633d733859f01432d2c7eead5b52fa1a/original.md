```julia
SaveIniSettingsToMemory() -> Ptr{Int8}
SaveIniSettingsToMemory(out_ini_size) -> Ptr{Int8}

```

Return a zero-terminated string with the .ini data which you can save by your own mean. call when io.WantSaveIniSettings is set, then save data by your own mean and clear io.WantSaveIniSettings.

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1068).
