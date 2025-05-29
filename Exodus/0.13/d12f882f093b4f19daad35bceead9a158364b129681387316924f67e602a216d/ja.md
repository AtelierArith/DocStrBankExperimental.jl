```julia
copy(
    exo::Exodus.ExodusDatabase,
    new_file_name::String;
    mesh_only_flag
)

```

ExodusDatabaseをコピーするために使用されます。現時点では、出力用の新しいExodusDatabaseを作成するための最良の方法です。すべてのputメソッドがラップされて適切にテストされているわけではありませんが、このメソッドはテストされています。
