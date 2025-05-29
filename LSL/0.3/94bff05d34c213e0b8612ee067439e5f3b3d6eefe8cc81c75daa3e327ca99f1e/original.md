```
resolve_bypred(predicate; minimum = 1, timeout = LSL_FOREVER)
```

Resolve all streams that match a given predicate.

Advanced query that allows to impose more conditions on the retrieved streams; the given string is an XPath 1.0 predicate for the <description> node (omitting the surrounding []'s), see also http://en.wikipedia.org/w/index.php?title=XPath_1.0&oldid=474981951.

Returns a vector of matching StreamInfo objects (with empty desc field), any of which can subsequently be used to open an inlet.

# Argumennts:

-`predicate::String`: Predicate string, e.g. "name='BioSemi'" or "type='EEG' and                      starts-with(name,'BioSemi') and count(description/desc/channels/channel)=32"

# Keyword arguments

-`minimum::Integer`: Return at least this many streams. -`timeout::Number`: A timeout of the operation, in seconds. If the timeout expires, less than                   the desired number of streams (possibly none) will be returned.             
