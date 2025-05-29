```
ansi_esc_status(status::IncrementalANSIEscape, c::Char) → status
ansi_esc_status(c::Char) → status
```

Return a `status` code indicating our position within an [ANSI terminal escape code](https://en.wikipedia.org/wiki/ANSI_escape_code).

# Examples

```jldoctest; prefix=:(using WidthLimitedIO)
julia> status = ansi_esc_status('m')   # ordinary character with no prior `status`
NONE::IncrementalANSIEscape = 0

julia> status = ansi_esc_status(status, '')  # start an escape sequence
ESCAPE1::IncrementalANSIEscape = 1

julia> status = ansi_esc_status(status, '[')   # CSI
ESCAPE::IncrementalANSIEscape = 2

julia> status = ansi_esc_status(status, '3')   # can be multiple digits
PARAMETER::IncrementalANSIEscape = 5

julia> status = ansi_esc_status(status, 'm')   # terminating final character
FINAL::IncrementalANSIEscape = 6

julia> status = ansi_esc_status(status, 'm')   # now 'm' is again an ordinary character
NONE::IncrementalANSIEscape = 0
```
