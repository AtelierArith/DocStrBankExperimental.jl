```julia
watch_folder(f::Function, dir=".")
```

フォルダーを再帰的に監視し、変更があった場合に通知します。ファイルの内容の変更も含まれます。コールバック関数 `f` に [`FileEvent`](@ref) が渡されます。

単一引数 `watch_folder(dir::AbstractString=".")` を使用して、フォルダーが変更されるまで **ブロッキングコール** を作成します（FileWatching 標準ライブラリのように）。

# 例

```julia
watch_folder(".") do event
    @info "何かが変更されました！" event
end
```

フォルダーを非同期に監視し、後でタスクを中断することもできます：

```julia
watch_task = @async watch_folder(".") do event
    @info "何かが変更されました！" event
end

sleep(5)

# フォルダーの監視を停止
schedule(watch_task, InterruptException(); error=true) 
```

# FileWatching stdlib との違い

  * `BetterFileWatching.watch_folder` は *再帰的* に動作し、サブフォルダーも監視されます。
  * `BetterFileWatching.watch_folder` はファイルの *内容* の変更も監視します。
  * BetterFileWatching.jl は [Deno.watchFs](https://doc.deno.land/builtin/stable#Deno.watchFs) に基づいており、[Deno_jll](https://github.com/JuliaBinaryWrappers/Deno_jll.jl) パッケージを通じて利用可能です。
