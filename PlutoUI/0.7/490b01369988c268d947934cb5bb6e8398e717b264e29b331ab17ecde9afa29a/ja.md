ブラウザからファイルとしてJuliaオブジェクトをダウンロードするためのボタン。

逆の操作を行うには[`FilePicker`](@ref)を参照してください。

# 例

```julia
DownloadButton("Roses are red,", "novel.txt")
```

```julia
DownloadButton(UInt8[0xff, 0xd8, 0xff, 0xe1, 0x00, 0x69], "raw.dat")
```

```julia
import JSON
DownloadButton(JSON.json(Dict("name" => "merlijn", "can_cook" => true)), "staff.json")
```

**ローカルファイル**をダウンロード可能にしたい場合は、ファイルのデータを`read`する必要があります：

```julia
let
    filename = "/Users/fonsi/Documents/mydata.csv"
    DownloadButton(read(filename), basename(filename))
end
```
