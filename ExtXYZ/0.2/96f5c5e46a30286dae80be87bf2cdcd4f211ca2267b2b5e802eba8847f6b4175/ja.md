このパッケージは、材料および分子モデリングで使用される拡張XYZファイル形式のパーサーおよびライターを実装した[extxyz](https://github.com/libAtoms/extxyz) CライブラリのJuliaバインディングを提供します。これは、extxyzリポジトリに設定された[仕様](https://github.com/libAtoms/extxyz#extended-xyz-specification-and-parsing-tools)に従っています。

## 基本的な使い方

4つの主要な関数がエクスポートされています：`read_frame()`と`write_frame()`はそれぞれ単一の構成（スナップショット）を読み書きするためのもので、`read_frames()`と`write_frames()`は軌道を読み書きするためのものです。すべての関数は、文字列のファイル名、オープンな`Base.IO`インスタンス、または（主に内部使用を意図した）C `FILE*`ポインタ（`Ptr{Cvoid}`型として保存）で動作できます。

```julia
using ExtXYZ

frame = read_frame("input.xyz")  # 単一の原子構成、Dict{String}{Any}として表現される
write_frame("output.xyz", frame) # 単一のフレームを`output.xyz`に書き込む

frame10 = read_frame("input.xyz", 10) # 特定のフレームを読み込む、ファイル内の最初のフレームを1からカウント

all_frames = read_frames("seq.xyz")  # すべてのフレームを読み込む、Vector{Dict{String}{Any}}を返す
frames = read_frames("seq.xyz", 1:4) # 特定のフレームの範囲

write_frames("output.xyz", frames, append=true) # 4つのフレームを出力に追加
```
