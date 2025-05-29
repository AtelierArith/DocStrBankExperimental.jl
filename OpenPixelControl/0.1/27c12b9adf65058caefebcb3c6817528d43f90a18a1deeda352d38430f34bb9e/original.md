setPixel(o,colors[, channel=0, command=0])

send pixel `colors` to the OPC server `o` on the given `channel` with given `command`.

# Input

  * `o::OpenPixelConnection` – the connection representing the server to send the colors to
  * `colors::Array{<:AbstractRGB}` – an array of RGB colors, each entry representing one pixel's color
  * `channel::Integer` – (`0`) determines the channel/strand `[1-255]` to send the values to. The default `0` refers to all channels
  * `command::Integer` – (`0`) command to use to send the pixel. The value `0` is the default by [openpixelcontrol.org](https://openpixelcontrol.org)
