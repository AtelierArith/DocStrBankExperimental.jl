allocframehdrs(io)

Allocate memory for headers for one frame of JavaSeis dataset.  Returns `Array{UInt8,2}`. For example, `hdrs = allocframehdrs(jsopen("data.js"))`.
