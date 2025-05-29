`artifact_reject(signal::TimeSeries, anoms::Vector{Integer}; epoch_length::Integer=30)`

An anomaly vector $\vec{x} \in \mathbb{N}^{n}$ is a sorted vector whose values are those epochs in an `TimeSeries` that contain  anomalies or artifacts. This function segments the TimeSeries and filters out all  epochs containing artifacts.
