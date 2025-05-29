```
function write_files(
    [f_write,] filenames::AbstractString...;
    mode::WriteMode = CreateOrIgnore(),
    use_cache::Bool = false, cache_dir::AbstractString = default_cache_dir(),
    create_dirs::Bool = true, delete_tmp_onerror::Bool=true,
    verbose::Bool = false
)
```

`filenames`に対して原子的な方法で書き込みを行います。これは、使用されるOSやファイルシステムに依存して最善を尽くすものです。

`mode`は既存のファイルの扱い方を決定します。これは[`CreateOrIgnore()`](@ref)（デフォルト）、[`CreateNew()`](@ref)、[`CreateOrReplace()`](@ref)、[`CreateOrModify()`](@ref)または[`ModifyExisting()`](@ref)のいずれかです。

書き込み関数`f_write`が指定されている場合、`f_create(temporary_filenames...)`が呼び出されます。`f_create`が例外をスローしなければ、ファイル`temporary_filenames`は`filenames`に名前が変更されます。そうでない場合、テンポラリファイルは削除されるか（`delete_tmp_onerror`が`true`の場合）、そのまま残されます（デバッグ目的など）。

すべての中間ステップのログを見るには、`ENV["JULIA_DEBUG"] = "ParallelProcessingTools"`を設定してください。

例えば：

```julia
write_files("foo.txt", "bar.txt", use_cache = true) do tmp_foo, tmp_bar
    write(tmp_foo, "Hello")
    write(tmp_bar, "World")
end
```

`write_files(f_write, filenames...)`は、ファイルが（再）書き込まれた場合は`filenames`を、何もすることがなかった場合は`nothing`を返します（`mode`に依存します）。

書き込み関数`f_write`が指定されていない場合、`write_files`はテンポラリファイル名を保持する[`FilesToWrite`](@ref)型のオブジェクトを返します。それを閉じると、上記のようにテンポラリファイルが`filenames`に名前変更されるか、削除されます。したがって

```julia
ftw = write_files("foo.txt", "bar.txt")
if !isnothing(ftw)
    try
        foo, bar = ftw
        write(foo, "Hello")
        write(bar, "World")
        close(ftw)
    catch err
        close(ftw, err)
        rethrow()
    end
end
```

は、上記の`write_files(f_write, ...)`を使用した例と同等です。

ファイルを変更する際、`write_files`は最初に既存のファイル`filenames`を`temporary_filenames`にコピーし、その後は上記のように動作します。

`use_cache`が`true`の場合、`temporary_filenames`は`cache_dir`に配置され、その後原子的に`filenames`に移動されます。そうでない場合、`filenames`の隣に配置されます（同じディレクトリ内に）。

`create_dirs`が`true`の場合、必要に応じてターゲットおよびキャッシュディレクトリのパスが作成されます。

`verbose`が`true`の場合、ファイル作成をログするためにログレベル`Logging.Info`を使用し、そうでない場合は`Logging.Debug`を使用します。

Linuxでは、`use_cache = true`および`cache_dir = "/dev/shm"`を設定することで、デフォルトのLinux RAMディスクを中間ディレクトリとして使用できます。

[`read_files`](@ref)および[`ParallelProcessingTools.default_cache_dir`](@ref)も参照してください。
