```
ansi_esc_status(status::IncrementalANSIEscape, c::Char) → status
ansi_esc_status(c::Char) → status
```

[ANSI端末エスケープコード](https://en.wikipedia.org/wiki/ANSI_escape_code)内の位置を示す`status`コードを返します。

# 例

```jldoctest; prefix=:(using WidthLimitedIO)
julia> status = ansi_esc_status('m')   # 以前の`status`がない普通の文字
NONE::IncrementalANSIEscape = 0

julia> status = ansi_esc_status(status, '')  # エスケープシーケンスの開始
ESCAPE1::IncrementalANSIEscape = 1

julia> status = ansi_esc_status(status, '[')   # CSI
ESCAPE::IncrementalANSIEscape = 2

julia> status = ansi_esc_status(status, '3')   # 複数桁の可能性
PARAMETER::IncrementalANSIEscape = 5

julia> status = ansi_esc_status(status, 'm')   # 終了する最終文字
FINAL::IncrementalANSIEscape = 6

julia> status = ansi_esc_status(status, 'm')   # 今や'm'は再び普通の文字
NONE::IncrementalANSIEscape = 0
```
