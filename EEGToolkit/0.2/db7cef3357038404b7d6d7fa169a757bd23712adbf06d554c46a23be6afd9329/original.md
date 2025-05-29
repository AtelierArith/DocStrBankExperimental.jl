filter*channels!(eeg::EEG, filter*function::Function)::Dict{String, TimeSeries}

Applies by reference a `filter_function` to the dictionary which maps channel  names to time series. 

Example: `filter_channel(eeg, p -> startswith(first(p), "C"))` would keep  only those EEG channels whose names begin with "C". 
