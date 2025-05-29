```julia
SaveIniSettingsToMemory() -> Ptr{Int8}
SaveIniSettingsToMemory(out_ini_size) -> Ptr{Int8}

```

ゼロ終端の文字列を返し、.ini データを含んでおり、自分の方法で保存できます。io.WantSaveIniSettings が設定されているときに呼び出し、自分の方法でデータを保存し、io.WantSaveIniSettings をクリアします。

[Upstream link](https://github.com/ocornut/imgui/blob/v1.91.8-docking/imgui.h#L1068).
