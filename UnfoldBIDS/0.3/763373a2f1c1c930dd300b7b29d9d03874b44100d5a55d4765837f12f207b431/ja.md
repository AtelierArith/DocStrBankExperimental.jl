```
save_results(results::DataFrame, bids_root::String; 
    derivatives_subfolder::String="Unfold",
    overwrite::Bool=false)
```

BIDSルートフォルダに展開モデルを保存するための関数。デフォルトで`derivatives_subfolder`（デフォルト = "Unfold"）を作成し、その後、BIDSに従って結果の各モデルを保存します。保存されたファイルへのパスの例: `bids_root/derivatives/Unfold/sub-XXX/eeg/sub-XXX_ses-XX_task-XXX_run-XX_unfold.jld2`

# キーワード

  * `derivatives_subfolder::String = "Unfold"`  指定されたサブフォルダを作成し、BIDSに従って展開モデルを保存します。
  * `overwrite::Bool = false`  既存のデータセットを上書きしません; trueに設定できます。
