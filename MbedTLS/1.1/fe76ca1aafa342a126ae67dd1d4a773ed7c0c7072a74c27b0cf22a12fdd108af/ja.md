`digest(kind::MDKind, msg::Vector{UInt8}, [key::Vector{UInt8}]) -> Vector{UInt8}`

指定されたタイプのダイジェストを与えられたメッセージ（バイト配列）に対して実行し、ダイジェストを含むバイト配列を返します。

オプションのキーが指定されている場合は、HMACダイジェストを実行します。
