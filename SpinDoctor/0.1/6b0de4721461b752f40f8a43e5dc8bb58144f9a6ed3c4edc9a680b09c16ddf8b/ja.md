```
VTKWriter(; nupdate = 1, dir = "output", filename = "solution")
```

`nupdate` タイムステップごとに磁化場を VTK ファイルに書き込みます。ファイルは ParaView データコレクションファイル (PVD) に保存されます。磁化の時系列は、`"$dir/$filename.pvd"` ファイルを開くことで ParaView で視覚化できます。コンパートメントにはラベルが付けられています。
