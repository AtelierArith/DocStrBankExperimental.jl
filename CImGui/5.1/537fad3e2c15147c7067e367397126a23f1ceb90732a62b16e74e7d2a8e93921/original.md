```julia
LoadIniSettingsFromDisk(ini_filename)

```

Call after CreateContext() and before the first call to NewFrame(). NewFrame() automatically calls LoadIniSettingsFromDisk(io.IniFilename).

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1065).
