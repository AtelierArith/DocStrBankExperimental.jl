filter*channels(eeg::EEG, filter*function::Function)::Dict{String, TimeSeries}

Applies a `filter_function` to the dictionary which maps channel  names to time series, and returns the filtered result.

Example: `filter_channel(eeg, p -> startswith(first(p), "C"))` would return  only those EEG channels whose names begin with "C". 
