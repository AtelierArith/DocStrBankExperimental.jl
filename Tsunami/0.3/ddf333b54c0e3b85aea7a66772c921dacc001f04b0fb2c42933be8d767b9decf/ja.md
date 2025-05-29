```
Checkpointer(folder = nothing) <: AbstractCallback
```

[`FluxModule`](@ref)とフィット状態を保存するためのヘルパークラスです。チェックポイントは、`ckpt_epoch=X_step=Y.jld2`という名前のJLD@ファイルとして保存されます。最後のチェックポイントへのシンボリックリンクも`ckpt_last.jld2`として作成されます。

`checkpointer = true`が[`fit!`](@ref)に渡されると、`Checkpointer`が自動的に作成されます。

`folder`が指定されていない場合、チェックポイントは実行ディレクトリ内の`checkpoints`という名前のフォルダーに保存されます。

関連情報: [`load_checkpoint`](@ref).

# 例

```julia
checkpointer = Checkpointer()
Tsunami.fit!(..., callbacks = [checkpointer])
```
