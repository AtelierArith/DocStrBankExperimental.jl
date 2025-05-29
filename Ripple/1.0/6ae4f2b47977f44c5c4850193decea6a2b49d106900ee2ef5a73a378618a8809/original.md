```
NxFile(
    header::NxHeader,
    channel_headers::Vector{NxChannelHeader}
    data_packets::Vector{NxPacket}
)
```

Object containing the Nx file header (for either NSx or NFX), a `Vector` of individual channel headers, and a `Vector` of [`NxPacket`](@ref)'s found in the file.
