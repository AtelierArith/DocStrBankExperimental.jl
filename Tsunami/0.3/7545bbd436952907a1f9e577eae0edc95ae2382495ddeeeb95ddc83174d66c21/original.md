```
Trainer(; kws...)
```

A type storing the training options to be passed to [`fit!`](@ref).

A `Trainer` object also contains a field `fit_state` of type [`FitState`](@ref) mantaining updated information about  the fit state during the execution of `fit!`.

# Constructor Arguments

  * **autodiff**: The automatic differentiation engine to use.                Possible values are `:zygote` and `:enzyme` . Default: `:zygote`.
  * **callbacks**: Pass a single or a list of callbacks. Default `nothing`.
  * **checkpointer**: If `true`, enable checkpointing.                   Default: `true`.
  * **default_root_dir** : Default path for logs and weights.                     Default: `pwd()`.
  * **fast_dev_run**: If set to `true` runs a single batch for train and validation to find any bugs.             Default: `false`.
  * **log_every_n_steps**: How often to log within steps. See also `logger`.            Default: `50`.
  * **logger**: If `true` use tensorboard for logging.           Every output of the `train_step` will be logged every 50 steps by default.           Set `log_every_n_steps` to change this.           Default: `true`.
  * **max_epochs**: Stop training once this number of epochs is reached.                Disabled by default (`nothing`).                If both `max_epochs` and `max_steps` are not specified,                defaults to `max_epochs = 1000`. To enable infinite training, set `max_epochs` = -1.               Default: `nothing`.
  * **max_steps**: Stop training after this number of steps.               Disabled by default (`-1`).               If `max_steps = -1` and `max_epochs = nothing`, will default to `max_epochs = 1000`.               To enable infinite training, set `max_epochs` to `-1`.              Default: `-1`.
  * **progress_bar**: It `true`, shows a progress bar during training.                  Default: `true`.
  * **val_every_n_epochs**: Perform a validation loop every after every N training epochs.                       The validation loop is in any case performed at the end of the last training epoch.                       Set to 0 or negative to disable validation.                       Default: `1`.

The constructor also take any of the [`Foil`](@ref)'s constructor arguments:

  * **accelerator**: Supports passing different accelerator types:

      * `:auto` (default): Automatically select a gpu if available, otherwise fallback on cpu.
      * `:gpu`: Like `:auto`, but will throw an error if no gpu is available.  In order for a gpu to be available, the corresponding package must be loaded (e.g. with `using CUDA`).  The trigger packages are `CUDA.jl` for Nvidia GPUs, `AMDGPU.jl` for AMD GPUs, and `Metal.jl` for Apple Silicon.
      * `:cpu`: Force using the cpu.

    See also the `devices` option.
  * **devices**: Pass an integer `n` to train on `n` devices (only `1` supported at the moment),   or a list of devices ids to train on specific devices (e.g. `[2]` to train on gpu with idx 2).   Ids indexing starts from `1`. If `nothing`, will use the default device    (see `MLDataDevices.gpu_device` documentation).    Default: `nothing`.
  * **precision**: Supports passing different precision types `(:bf16, :f16, :f32, :f64)`,    where `:bf16` is BFloat16, `:f16` is Float16, `:f32` is Float32, and `:f64` is Float64.   Default: `:f32`.

# Fields

Besides most of the constructor arguments, a `Trainer` object also contains the following fields:

  * **fit_state**: A [`FitState`](@ref) object storing the state of execution during a call to [`fit!`](@ref).
  * **foil**: A [`Foil`](@ref) object.
  * **loggers**: A list of loggers.
  * **lr_schedulers**: The learning rate schedulers used for training.
  * **optimisers**: The optimisers used for training.

# Examples

```julia
trainer = Trainer(max_epochs = 10, 
                  accelerator = :cpu,
                  checkpointer = true,
                  logger = true)

Tsunami.fit!(model, trainer, train_dataloader, val_dataloader)
```
