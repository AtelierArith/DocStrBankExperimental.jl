```
vtk_grid(f::Function, args...; kwargs...)
```

VTKファイルを作成し、`f`を適用します。呼び出しの終了時にファイルは自動的に閉じられます。

これにより、VTKファイルを作成するためのdoブロック構文を使用できます：

```julia
saved_files = vtk_grid(args...; kwargs...) do vtk
    # `vtk`ファイルハンドラで作業を行う
end
```
