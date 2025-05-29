```
_save_trial_results(trial_df::DataFrame, datum_name::String, output_dir::String, 
                    streams::Dict{String, CSVFiles.CSVFileSaveStream{IOStream}})
```

保存されたシミュレーション結果を `trial_df` から試行 `trialnum` のファイルに `output_dir` ディレクトリに保存します。
