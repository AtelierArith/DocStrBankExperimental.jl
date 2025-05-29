```
esc = h5_get_ESC(filename::String; T::Type = ComplexF32)
```

ファイルからESC（エミュレートされた単一コイル）データの`Array`を返します。

HDF5.jlはデータをPythonのh5pyとは異なる方法で読み取ります。これは重要で、fastMRIの論文ではデータセットが特定の次元を持つと述べていますが、次元はPythonと比較してJuliaでは入れ替わっているため、以下の関数で`permutedims`を呼び出しています。
