```julia
load_magnetic_field(
    file::String;
    include_dirs
) -> HallThruster.MagneticField

```

ファイルへのパスを指定すると、そのファイルのデータから`MagneticField`をロードします。現在の作業ディレクトリと、`include_dirs`に渡された追加のディレクトリを検索します。
