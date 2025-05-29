```julia
run_model_epochs(
    inmodel::EasyABM.GraphModel;
    steps_per_epoch,
    num_epochs,
    step_rule,
    save_to_folder
)

```

`num_epochs` 回のエポックのシミュレーションを実行します。各エポックは `steps_per_epoch` 回のステップで構成されます。各エポックのモデルは入力モデルのディープコピーであり、.jld2 ファイルとして保存されます。
