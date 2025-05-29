set_postprocessing(inlet::StreamInlet, flags::UInt32)

Set post-processing flags to use.

By default, the inlet performs NO post-processing and returns the ground-truth time stamps, which can then be manually synchronized using time_correction(), and then  smoothed/dejittered if desired. This function allows automating these two and possibly more operations.

Warning: when you enable this, you will no longer receive or be able to recover the original time stamps.

Function may throw an argument error if unknown flags are supplied.

# Arguments:

`flags::UInt32`: An integer that is the result of bitwise OR'ing one or more options from                  processing*options*t together. A good setting is to use post_ALL.
