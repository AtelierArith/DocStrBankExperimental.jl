`digest!(kind::MDKind, msg::Vector{UInt8}, [key::Vector{UInt8}, ], buffer::Vector{UInt8})`

ダイジェストを `buffer` に格納する `digest` のインプレースバージョンです。

バッファがダイジェストを格納するのに十分な長さであることを保証するのはユーザーの責任です。 `get_size(kind::MDKind)` は適切なサイズを返します。
