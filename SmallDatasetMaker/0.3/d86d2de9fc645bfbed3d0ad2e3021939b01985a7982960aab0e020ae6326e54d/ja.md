`unzip_file(target_path)` は、`target_path` にあるファイルを現在のディレクトリに解凍し、その元の名前を保持します。

# 注意！

もし `SmallDatasetMaker` や現在作業しているディレクトリ以外のパッケージの下で `target_path` をロードするつもりであれば、`abspath(args::String...)` または `abspath(ACertainImportedPackage, args::String...)` を適用する必要があります。つまり、`target_path = SmallDatasetMaker.abspath(...)` です。
