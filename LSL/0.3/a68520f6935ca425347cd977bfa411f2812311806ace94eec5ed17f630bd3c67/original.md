```
resolve_streams(;timeout = 1.0)
```

Returns all currently available streams from any outlet on the network. 

The network is usually the subnet specified at the local router, but may also include a group of machines visible to each other via multicast packets (given that the network supports it), or list of hostnames. These details may optionally be customized by the experimenter in a configuration file (see Network Connectivity in the LSL wiki).  

Returns a vector of StreamInfo objects (with empty desc field), any of which can subsequently be used to open an inlet. The full description can be retrieved from the inlet.

# Keyword arguments:

-`timeout`: The waiting time for the operation, in seconds, to search for streams. Warning:             If this is too short (<0.5s) only a subset (or none) of the outlets that are             present on the network may be returned.
