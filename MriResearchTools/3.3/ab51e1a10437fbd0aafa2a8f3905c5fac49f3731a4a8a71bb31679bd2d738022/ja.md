```
readmag(filename; rescale=false, keyargs...)
```

NIfTIのマグニチュードを読み込み、サニティチェックと[0;1]へのオプションのリスケーリングを行います。

# 例

```julia-repl
julia> mag = readmag("mag.nii")
```

### オプションのkeyargsは`niread`に転送されます：

Base.Docs.DocStr(svec("    niread(file; mmap=false, mode=\"r\")\n\nNIfTIファイルをNIVolumeに読み込みます。`mmap=true`を設定すると、ボリュームをメモリマップします。\n"), nothing, Dict{Symbol, Any}(:typesig => Tuple{AbstractString}, :module => NIfTI, :linenumber => 234, :binding => NIfTI.niread, :path => "/Users/atelierarith/.julia/packages/NIfTI/ytzbJ/src/NIfTI.jl")) ```
