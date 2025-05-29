setPixel(o,r,b,g[, channel=0, command=0])

send pixel colors represented by three `NTuples{N,UInt8}` of same length to the OPC server `o` on the given `channel` with given `command`.

# Input

  * `o::OpenPixelConnection` – the connection representing the server to send the colors to
  * `r`,`g`,`b::NTuple{N,UInt8}` – three `NTuples` of `UInt8` with same length `N` representing the 8bit an array of RGB colors, each set of entries representing one pixel's color
  * `channel::Integer` – (`0`) determines the channel/strand `[1-255]` to send the values to. The default `0` refers to all channels
  * `command::Integer` – (`0`) command to use to send the pixel. The value `0` is the default by [openpixelcontrol.org](https://openpixelcontrol.org)
