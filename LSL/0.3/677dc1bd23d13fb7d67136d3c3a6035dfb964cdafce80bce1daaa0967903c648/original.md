smoothing_halftime(inlet::StreamInlet, value)

Override the half-time (forget factor) of the time-stamp smoothing.

The default is 90 seconds unless a different value is set in the config file. Using a longer window will yield lower jitter in the time stamps, but longer windows will have trouble tracking changes in the clock rate (usually due to temperature changes); the default is able to track changes up to 10 degrees C per minute sufficiently well.

# Arguments

`value::Number`: The new value, in seconds. This is the time after which a past sample will                  be weighted by 1/2 in the exponential smoothing window.
