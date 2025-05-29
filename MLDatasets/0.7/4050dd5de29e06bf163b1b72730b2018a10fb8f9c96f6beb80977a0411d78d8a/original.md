```
TemporalBrains(; dir = nothing, threshold_value = 0.6)
```

The TemporalBrains dataset contains a collection of temporal brain networks (as `TemporalSnapshotsGraph`s) of 1000 subjects obtained from resting-state fMRI data from the [Human Connectome Project (HCP)](https://www.humanconnectome.org/study/hcp-young-adult/document/extensively-processed-fmri-data-documentation).

The number of nodes is fixed for each of the 27 snapshots at 102, while the edges change over time.

For each `Graph` snapshot, the feature of a node represents the average activation of the node during that snapshot and it is contained in `Graphs.node_data`.

Each `TemporalSnapshotsGraph` has a label representing their gender ("M" for male and "F" for female) and age range (22-25, 26-30, 31-35 and 36+) contained as a named tuple in `graph_data`.

The `threshold_value` is used to binarize the edge weights and is set to 0.6 by default.
