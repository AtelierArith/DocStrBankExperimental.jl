```julia
watch_file(f::Function, filename::AbstractString)
```

ファイルの変更を再帰的に監視します。変更が発生したときに、[`FileEvent`](@ref) がコールバック関数 `f` に渡されます。

単一引数の `watch_file(filename::AbstractString)` を使用して、ファイルが変更されるまで **ブロッキングコール** を作成します（FileWatching 標準ライブラリのように）。

# 例

```julia
watch_file("file.txt") do event
    @info "何かが変更されました！" event
end
```

ファイルを非同期に監視し、後でタスクを中断することができます：

```julia
watch_task = @async watch_file("file.txt") do event
    @info "何かが変更されました！" event
end

sleep(5)

# ファイルの監視を停止
schedule(watch_task, InterruptException(); error=true) 
```

# FileWatching stdlib との違い

  * BetterFileWatching.jl は [Deno.watchFs](https://doc.deno.land/builtin/stable#Deno.watchFs) に基づいており、[Deno_jll](https://github.com/JuliaBinaryWrappers/Deno_jll.jl) パッケージを通じて利用可能です。
