```
TranscodingStream(codec::Codec, stream::IO;
                  bufsize::Integer=16384,
                  stop_on_end::Bool=false,
                  sharedbuf::Bool=(stream isa TranscodingStream))
```

Create a transcoding stream with `codec` and `stream`.

A `TranscodingStream` object wraps an input/output stream object `stream`, and transcodes the byte stream using `codec`. It is a subtype of `IO` and supports most of the I/O functions in the standard library.

See the docs ([https://bicycle1885.github.io/TranscodingStreams.jl/stable/](https://bicycle1885.github.io/TranscodingStreams.jl/stable/)) for available codecs, examples, and more details of the type.

## Arguments

  * `codec`:   The data transcoder. The transcoding stream does the initialization and   finalization of `codec`. Therefore, a codec object is not reusable once it   is passed to a transcoding stream.
  * `stream`:   The wrapped stream. It must be opened before passed to the constructor.
  * `bufsize`:   The initial buffer size (the default size is 16KiB). The buffer may be   extended whenever `codec` requests so.
  * `stop_on_end`:   The flag to stop reading on `:end` return code from `codec`.  The   transcoded data are readable even after stopping transcoding process.  With   this flag on, `stream` is not closed when the wrapper stream is closed with   `close`.  Note that if reading some extra data may be read from `stream` into an   internal buffer, and thus `stream` must be a `TranscodingStream` object and   `sharedbuf` must be `true` to reuse `stream`.
  * `sharedbuf`:   The flag to share buffers between adjacent transcoding streams.  The value   must be `false` if `stream` is not a `TranscodingStream` object.

## Examples

```jldoctest
julia> using TranscodingStreams

julia> file = open(joinpath(dirname(dirname(pathof(TranscodingStreams))), "README.md"));

julia> stream = TranscodingStream(Noop(), file);

julia> readline(file)
"TranscodingStreams.jl"

julia> close(stream)
```
