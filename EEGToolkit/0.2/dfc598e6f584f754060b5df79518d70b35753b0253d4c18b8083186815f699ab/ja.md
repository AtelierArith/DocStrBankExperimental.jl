`plot_eeg(eeg::EEG, s::Integer, e::Integer; channels::Vector{String}=[""], spacing::AbstractFloat=1.5)`

エポック `s` からエポック `e` までの EEG チャンネルをプロットします。特定のチャンネルは `channels` キーワード引数で選択できます。`spacing` 引数は EEG 信号の正規化における追加の要因であり、プロット内の各信号間の垂直距離は `spacing` に比例して増加します。
