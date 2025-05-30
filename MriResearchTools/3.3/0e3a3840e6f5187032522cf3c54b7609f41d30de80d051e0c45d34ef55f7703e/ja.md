```
write_emptynii(size, path; datatype=Float32, header=NIVolume(zeros(datatype, 1)).header)
```

ディスクに空のNIfTI画像を書き込み、メモリマップアクセスに使用できます。

# 例

```julia-repl
julia> vol = write_emptynii((64,64,64), "empty.nii")
julia> vol.raw[:,:,1] .= ones(64,64) # ディスク上のmmappedファイルを同期
```

警告: MRIcroはInt32、Int64、Float32、Float64のタイプの画像のみを開くことができます。
