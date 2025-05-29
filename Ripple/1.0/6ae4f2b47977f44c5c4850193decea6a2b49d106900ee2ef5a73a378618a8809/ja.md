```
NxFile(
    header::NxHeader,
    channel_headers::Vector{NxChannelHeader}
    data_packets::Vector{NxPacket}
)
```

NSxまたはNFXのためのNxファイルヘッダー、個々のチャネルヘッダーの`Vector`、およびファイル内で見つかった[`NxPacket`](@ref)の`Vector`を含むオブジェクト。
