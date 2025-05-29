samples_available(inlet::StreamInlet)

Query whether samples are currently available for immediate pickup.

Note that it is not a good idea to use samples*available() to determine whether a pull**() call would block: to be sure, set the pull timeout to 0.0 or an acceptably low value. If the underlying implementation supports it, the value will be the number of samples available (otherwise it will be 1 or 0).
