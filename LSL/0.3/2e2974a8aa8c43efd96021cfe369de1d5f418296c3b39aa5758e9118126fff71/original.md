```
resolve_byprop(prop, value; minimum = 1, timeout = LSL_FOREVER)
```

Resolve all streams with a specific value for a given property.

If the goal is to resolve a specific stream, this method is preferred over resolving all streams and then selecting the desired one.

Returns a vector of matching StreamInfo objects (with empty desc field), any of which can subsequently be used to open an inlet.

# Arguments

-`prop::String`: The StreamInfo property that should have a specific value (e.g., "name",                 "type", "source_id", or "desc/manufaturer"). -`value::String`: The string value that the property should have (e.g., "EEG" as the type                  property).

# Keyword arguments

-`minimum::Integer`: Return at least this many streams. -`timeout::Number`: A timeout of the operation, in seconds. If the timeout expires, less than                    the desired number of streams (possibly none) will be returned.                   

# Example

results = resolve_byprop("type", "EEG")                  
