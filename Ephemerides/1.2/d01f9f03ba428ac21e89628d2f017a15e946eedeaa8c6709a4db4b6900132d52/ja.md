```
EphemerisProvider(file::String)
EphemerisProvider(files::Vector{String})
```

`files`で指定された単一または複数のバイナリエフェメリスカーネルファイルをロードすることによって`EphemerisProvider`インスタンスを作成します。現在、NAIFダブル精度配列ファイル（DAF）カーネル（すなわち、SPKおよびPCK）のみが受け入れられます。

### 例

```julia-repl
julia> eph = EphemerisProvider("PATH_TO_KERNEL")
EphemerisProvider([...])

julia> eph = EphemerisProvider(["PATH_TO_KERNEL_1", "PATH_TO_KERNEL_2"])
EphemerisProvider([])
```
