```julia
LoadIniSettingsFromDisk(ini_filename)

```

CreateContext() の後、NewFrame() の最初の呼び出しの前に呼び出します。NewFrame() は自動的に LoadIniSettingsFromDisk(io.IniFilename) を呼び出します。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1065).
