filter*channels!(eeg::EEG, filter*function::Function)::Dict{String, TimeSeries}

辞書に対して `filter_function` を参照渡しで適用し、チャネル名を時系列にマッピングします。

例: `filter_channel(eeg, p -> startswith(first(p), "C"))` は、名前が "C" で始まる EEG チャネルのみを保持します。
