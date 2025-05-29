```
function read_files(
    [f_read, ], filenames::AbstractString...;
    use_cache::Bool = true, cache_dir::AbstractString = default_cache_dir(),
    create_cachedir::Bool = true, delete_tmp_onerror::Bool=true,
    verbose::Bool = false
)
```

`filenames`を原子的な方法で読み込みます（すなわち、すべての`filenames`が存在する場合のみ）。これは、使用されるOSおよびファイルシステムに依存して、最善の努力に基づいています。

読み取り関数`f_read`が指定されている場合、`f_read(filenames...)`が呼び出されます。`f_read`の戻り値がそのまま返されます。

`use_cache`が`true`の場合、ファイルは最初にキャッシュディレクトリ`cache_dir`に一時的な名前でコピーされ、その後`f_read(temporary_filenames...)`を介して読み取られます。一時ファイルは、`f_read`が終了した後に削除されます（ただし、読み取り中に例外がスローされ、`delete_tmp_onerror`が`false`に設定されている場合を除きます）。

すべての中間ステップのログを表示するには、`ENV["JULIA_DEBUG"] = "ParallelProcessingTools"`を設定してください。

例えば：

```julia
write("foo.txt", "Hello"); write("bar.txt", "World")

result = read_files("foo.txt", "bar.txt", use_cache = true) do foo, bar
    read(foo, String) * " " * read(bar, String)
end
```

読み取り関数`f_read`が指定されていない場合、`read_files`は一時ファイル名を保持する型[`FilesToRead`](@ref)のオブジェクトを返します。それを閉じると、上記のように一時ファイルがクリーンアップされます。したがって、

```julia
ftr = read_files("foo.txt", "bar.txt"; use_cache = true)
result = try
    foo, bar = collect(ftr)
    data_read = read(foo, String) * " " * read(bar, String)
    close(ftr)
    data_read
catch err
    close(ftr, err)
    rethrow()
end
```

は、上記の`read_files(f_read, ...)`を使用した例と同等です。

`create_cachedir`が`true`の場合、`cache_dir`はまだ存在しない場合に作成されます。

`verbose`が`true`の場合、ファイル読み取りのログに`Logging.Info`のログレベルを使用し、そうでない場合は`Logging.Debug`を使用します。

Linuxでは、`use_cache = true`および`cache_dir = "/dev/shm"`を設定して、デフォルトのLinux RAMディスクを中間ディレクトリとして使用できます。

[`write_files`](@ref)および[`ParallelProcessingTools.default_cache_dir`](@ref)も参照してください。
