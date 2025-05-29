```
abstract type DecodeOptions
```

データをデコードするためのオプション。

プロパティは読み取り用に公開されています。すべての `DecodeOptions` は、すべてのプロパティを引数として受け取るキーワード引数コンストラクタを持っています。すべての `DecodeOptions` には `codec::Codec` プロパティがあります。

型 `T <: DecodeOptions` が実装する必要のあるメソッド：

  * `try_find_decoded_size(::T, src::AbstractVector{UInt8})::Union{Nothing, Int64}`
  * `try_decode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}`

実装するためのオプションメソッド：

  * `is_thread_safe(::T)::Bool`: デフォルトは `false` です。
  * `try_resize_decode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}, max_size::Int64; kwargs...)::Union{Nothing, Int64}`: デフォルトでは `try_decode!` と `try_find_decoded_size` を使用します。
