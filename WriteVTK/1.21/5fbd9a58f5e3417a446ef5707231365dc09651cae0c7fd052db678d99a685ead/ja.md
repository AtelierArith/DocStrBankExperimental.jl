```
Base.close(vtk::VTKFile) -> Vector{String}
```

VTKファイルを書き込み、閉じます。

書き込まれたVTKファイルへのパスのリストを返します（通常は1つのファイルですが、例えば`MultiblockFile`の場合は複数になることがあります）。

---

```
Base.close(vtm::MultiblockFile) -> Vector{String}
```

マルチブロックファイル（`.vtm`）を保存して閉じます。マルチブロックファイルに含まれるVTKファイルも保存されます。
