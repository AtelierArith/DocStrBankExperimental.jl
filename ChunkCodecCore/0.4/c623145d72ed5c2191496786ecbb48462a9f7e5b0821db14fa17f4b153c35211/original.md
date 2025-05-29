```
abstract type Codec
```

Required information to decode encoded data.

Properties are public for reading.

Required methods for a type `T <: Codec` to implement:

  * `decode_options(::T)::DecodeOptions`

Optional methods to implement:

  * `can_concatenate(::T)::Bool`: defaults to `false`.
