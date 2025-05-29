`analyze_eeg(signal::Vector{<:AbstractFloat}, fs::Integer)::Spectrogram`

Perform a standardized analysis of an EEG signal. This analysis procedure  succesfully replicated results from Washington State University in collaboration with the developer's laboratory at UPenn. 

The standardized procedure is as follows: split the signal into 30-sec epochs, each of which is split into 5-sec sub-epochs. Each epoch's spectrum is the  aggregated spectra from its sub-epochs; the signal's spectrum is the aggregated  spectra from its epochs.
