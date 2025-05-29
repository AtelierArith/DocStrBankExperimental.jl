computes the power injection of each bus in the network, with a focus on the needs of Power Flow solvers.

excludes voltage-dependent components (e.g. shunts), these should be addressed as needed by the calling functions.  note that voltage dependent components are resolved during an AC Power Flow solve and are not static.

data should be a PowerModels network data model
