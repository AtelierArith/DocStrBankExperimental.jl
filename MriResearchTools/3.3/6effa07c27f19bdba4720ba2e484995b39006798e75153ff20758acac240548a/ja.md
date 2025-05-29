```
readphase(filename; rescale=true, fix_ge=false, keyargs...)
```

NIfTI位相を読み込み、サニティチェックと[-π;π]へのオプションの再スケーリングを行います。GEに関する警告: `fix_ge=true`が必要であり、すべての2番目のスライスにπを追加します。

# 例

```julia-repl
julia> phase = readphase("phase.nii")
```

### オプションのkeyargsは`niread`に転送されます:

Base.Docs.DocStr(svec("    niread(file; mmap=false, mode=\"r\")\n\nNIfTIファイルをNIVolumeに読み込みます。`mmap=true`を設定すると、ボリュームをメモリマップします。\n"), nothing, Dict{Symbol, Any}(:typesig => Tuple{AbstractString}, :module => NIfTI, :linenumber => 234, :binding => NIfTI.niread, :path => "/home/terasaki/.julia/packages/NIfTI/ytzbJ/src/NIfTI.jl")) ```
