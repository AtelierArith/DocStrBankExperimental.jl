```
Trainer(; kws...)
```

トレーニングオプションを [`fit!`](@ref) に渡すための型です。

`Trainer` オブジェクトは、`fit!` の実行中にフィット状態に関する更新情報を保持する [`FitState`](@ref) 型のフィールド `fit_state` も含まれています。

# コンストラクタ引数

  * **autodiff**: 使用する自動微分エンジン。可能な値は `:zygote` と `:enzyme` です。デフォルト: `:zygote`。
  * **callbacks**: 単一またはリストのコールバックを渡します。デフォルト `nothing`。
  * **checkpointer**: `true` の場合、チェックポイントを有効にします。デフォルト: `true`。
  * **default*root*dir** : ログと重みのデフォルトパス。デフォルト: `pwd()`。
  * **fast*dev*run**: `true` に設定すると、トレーニングと検証のために単一のバッチを実行してバグを見つけます。デフォルト: `false`。
  * **log*every*n_steps**: ステップ内でのログの頻度。`logger` も参照してください。デフォルト: `50`。
  * **logger**: `true` の場合、ログに tensorboard を使用します。`train_step` のすべての出力はデフォルトで50ステップごとにログされます。これを変更するには `log_every_n_steps` を設定します。デフォルト: `true`。
  * **max_epochs**: このエポック数に達したらトレーニングを停止します。デフォルトでは無効 (`nothing`) です。`max_epochs` と `max_steps` の両方が指定されていない場合、デフォルトは `max_epochs = 1000` です。無限トレーニングを有効にするには、`max_epochs` を -1 に設定します。デフォルト: `nothing`。
  * **max_steps**: このステップ数に達したらトレーニングを停止します。デフォルトでは無効 (`-1`) です。`max_steps = -1` かつ `max_epochs = nothing` の場合、デフォルトは `max_epochs = 1000` です。無限トレーニングを有効にするには、`max_epochs` を -1 に設定します。デフォルト: `-1`。
  * **progress_bar**: `true` の場合、トレーニング中にプログレスバーを表示します。デフォルト: `true`。
  * **val*every*n_epochs**: N エポックごとに検証ループを実行します。検証ループは、最後のトレーニングエポックの終了時にも必ず実行されます。検証を無効にするには、0 または負の値に設定します。デフォルト: `1`。

コンストラクタは、[`Foil`](@ref) のコンストラクタ引数のいずれかも受け取ります：

  * **accelerator**: 異なるアクセラレータタイプを渡すことをサポートします：

      * `:auto` (デフォルト): 利用可能な場合は自動的に GPU を選択し、そうでない場合は CPU にフォールバックします。
      * `:gpu`: `:auto` のように、GPU が利用できない場合はエラーをスローします。GPU が利用可能であるためには、対応するパッケージがロードされている必要があります（例: `using CUDA`）。トリガーパッケージは、Nvidia GPU 用の `CUDA.jl`、AMD GPU 用の `AMDGPU.jl`、Apple Silicon 用の `Metal.jl` です。
      * `:cpu`: CPU の使用を強制します。

    `devices` オプションも参照してください。
  * **devices**: `n` デバイスでトレーニングするために整数 `n` を渡すか、特定のデバイスでトレーニングするためのデバイス ID のリストを渡します（例: `[2]` はインデックス 2 の GPU でトレーニングします）。ID のインデックスは `1` から始まります。`nothing` の場合、デフォルトデバイスを使用します（`MLDataDevices.gpu_device` ドキュメントを参照）。デフォルト: `nothing`。
  * **precision**: 異なる精度タイプ `(:bf16, :f16, :f32, :f64)` を渡すことをサポートします。ここで `:bf16` は BFloat16、`:f16` は Float16、`:f32` は Float32、`:f64` は Float64 です。デフォルト: `:f32`。

# フィールド

コンストラクタ引数のほとんどに加えて、`Trainer` オブジェクトは次のフィールドも含まれています：

  * **fit_state**: [`FitState`](@ref) オブジェクトで、[`fit!`](@ref) の呼び出し中の実行状態を保存します。
  * **foil**: [`Foil`](@ref) オブジェクト。
  * **loggers**: ロガーのリスト。
  * **lr_schedulers**: トレーニングに使用される学習率スケジューラ。
  * **optimisers**: トレーニングに使用される最適化手法。

# 例

```julia
trainer = Trainer(max_epochs = 10, 
                  accelerator = :cpu,
                  checkpointer = true,
                  logger = true)

Tsunami.fit!(model, trainer, train_dataloader, val_dataloader)
```
