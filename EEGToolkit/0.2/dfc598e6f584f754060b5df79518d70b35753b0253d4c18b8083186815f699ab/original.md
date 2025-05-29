`plot_eeg(eeg::EEG, s::Integer, e::Integer; channels::Vector{String}=[""], spacing::AbstractFloat=1.5)`

Plots EEG channels from epoch `s` to epoch `e`. Specific channels may be selected with the `channels` karg. The `spacing` argument is an added factor in the normalization of the EEG signals - the vertical distance between each signal in the plot grows proportionally to `spacing`.
