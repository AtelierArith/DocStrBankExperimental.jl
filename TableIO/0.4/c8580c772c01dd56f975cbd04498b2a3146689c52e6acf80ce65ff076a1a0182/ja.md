```
read_table(file_picker:: Dict, args...; kwargs...)
```

PlutoUI.jlのFilePickerから表形式データを読み取ります。

使用法（Pluto.jlノートブック内）：

```
using PlutoUI, TableIO, DataFrames
using XLSX # アップロードされたファイル形式に必要なパッケージをインポート
@bind f PlutoUI.FilePicker()
df = DataFrame(read_table(f); copycols=false)
```
