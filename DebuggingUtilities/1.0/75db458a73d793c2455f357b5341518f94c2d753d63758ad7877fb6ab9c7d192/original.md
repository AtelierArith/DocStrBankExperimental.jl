`time_showline(filename)` is equivalent to `include(filename)`, except that it also analyzes the time expended on each expression within the file. Once finished, it displays the file-offset (in characters), elapsed time, and expression in order of increasing duration.  This can help you identify bottlenecks in execution.

This is less useful now that julia has package precompilation, but can still be handy on occasion.
