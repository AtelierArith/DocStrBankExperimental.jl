filter*channels(eeg::EEG, filter*function::Function)::Dict{String, TimeSeries}

`filter_function`をチャネル名を時系列にマッピングする辞書に適用し、フィルタリングされた結果を返します。

例: `filter_channel(eeg, p -> startswith(first(p), "C"))` は、名前が "C" で始まるEEGチャネルのみを返します。
