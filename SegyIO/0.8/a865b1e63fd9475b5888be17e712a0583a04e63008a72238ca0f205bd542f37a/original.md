set_header!(block, header, value)

Set the 'header' field in 'block' to 'value', where 'header' is either a string or symbol of a valid field in BinaryTraceHeader.

If 'value' is an Int, it will be applied to each header. If 'value' is a vector, the i-th 'value' will be set in the i-th traceheader.

# Example

set*header!(block, "SourceX", 100) set*header!(block, :SourceY, Array(1:100))
