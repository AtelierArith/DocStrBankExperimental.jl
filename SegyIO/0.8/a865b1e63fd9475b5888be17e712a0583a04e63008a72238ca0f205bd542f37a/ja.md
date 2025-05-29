set_header!(block, header, value)

'block'の'header'フィールドを'value'に設定します。'header'はBinaryTraceHeaderの有効なフィールドの文字列またはシンボルです。

'value'がIntの場合、各ヘッダーに適用されます。'value'がベクトルの場合、i番目の'value'がi番目のtraceheaderに設定されます。

# 例

set*header!(block, "SourceX", 100) set*header!(block, :SourceY, Array(1:100))
