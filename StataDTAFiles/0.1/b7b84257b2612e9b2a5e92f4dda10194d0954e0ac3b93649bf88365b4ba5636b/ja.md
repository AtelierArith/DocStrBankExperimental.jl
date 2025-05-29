```julia
struct DTAFile{T<:NamedTuple, B<:StataDTAFiles.ByteOrderIO}
```

データ自体を除くすべてが読み込まれたStata DTAファイルの表現。

データ（行）は、イテレーションインターフェースを使用して`NamedTuple`として読み込むことができます。
