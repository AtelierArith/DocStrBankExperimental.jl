使用法: fileheader = read_traceheader(s::IO, keys = Array{String,1}; bigendian::Bool = true)

現在のストリーム's'の位置から形成されたバイナリトレースヘッダーを返し、'keys'で示されたヘッダー値のみを読み取ります。
