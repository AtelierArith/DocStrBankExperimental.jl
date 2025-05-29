```
BlobTree(root)
```

`BlobTree` is a "directory tree" like hierarchy which may have `Blob`s and `BlobTree`s as children.

The tree implements the `AbstracTrees.children()` interface and may be indexed with paths to traverse the hierarchy down to the leaves ("files") which are of type `Blob`. Individual leaves may be `open()`ed as various Julia types.

# Example

Normally you'd construct these via the [`dataset`](@ref) function which takes care of constructing the correct `root` object. However, here's a direct demonstration:

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
