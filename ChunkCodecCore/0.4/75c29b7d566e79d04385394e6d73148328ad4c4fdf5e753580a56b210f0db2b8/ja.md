```
abstract type EncodeOptions
```

データをエンコードするためのオプション。

プロパティは読み取り用に公開されています。すべての `EncodeOptions` は、すべてのプロパティを引数として受け取るキーワード引数コンストラクタを持っています。すべての `EncodeOptions` には `codec::Codec` プロパティがあります。

型 `T <: EncodeOptions` が実装する必要のあるメソッド：

  * `decoded_size_range(::T)::StepRange{Int64, Int64}`
  * `encode_bound(::T, src_size::Int64)::Int64`
  * `try_encode!(::T, dst::AbstractVector{UInt8}, src::AbstractVector{UInt8}; kwargs...)::Union{Nothing, Int64}`

実装するためのオプションのメソッド：

  * `is_thread_safe(::T)::Bool`: デフォルトは `false`。
