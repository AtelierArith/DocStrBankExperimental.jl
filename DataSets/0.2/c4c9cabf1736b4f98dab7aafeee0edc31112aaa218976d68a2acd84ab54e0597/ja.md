```
BlobTree(root)
```

`BlobTree`は、`Blob`や`BlobTree`を子として持つことができる「ディレクトリツリー」のような階層です。

このツリーは`AbstracTrees.children()`インターフェースを実装しており、パスでインデックスを付けて階層を下にたどり、葉（「ファイル」）に到達することができます。葉は`Blob`型であり、個々の葉はさまざまなJulia型として`open()`できます。

# 例

通常、これらは[`dataset`](@ref)関数を介して構築され、正しい`root`オブジェクトの構築を処理します。しかし、ここでは直接のデモを示します：

```
julia> tree = BlobTree(DataSets.FileSystemRoot(dirname(pathof(DataSets))), path"../test/data")
📂 Tree ../test/data @ /home/chris/.julia/dev/DataSets/src
 📁 csvset
 📄 file.txt
 📄 foo.txt
 📄 people.csv.gz

julia> tree["csvset"]
📂 Tree ../test/data/csvset @ /home/chris/.julia/dev/DataSets/src
 📄 1.csv
 📄 2.csv

julia> tree[path"csvset"]
📂 Tree ../test/data/csvset @ /home/chris/.julia/dev/DataSets/src
 📄 1.csv
 📄 2.csv
```
