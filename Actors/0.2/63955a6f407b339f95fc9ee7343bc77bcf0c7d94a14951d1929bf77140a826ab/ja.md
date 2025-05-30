```
request(lk::Link, msg::Msg; full=false, timeout::Real=5.0)
request(lk::Link, M::Type{<:Msg}, args...; kwargs...)
```

アクターにメッセージを送信し、ブロックして結果を受信して返します。

# 引数

  * `lk::Link`: アクターリンク、または `name::Symbol`（登録されている場合）、
  * `msg::Msg`: メッセージ、
  * `Msg::Type{<:Msg}`: メッセージタイプ、
  * `args...`: `Msg`へのオプション引数、
  * `full`: `true`の場合、完全な [`Response`](@ref) メッセージを返します。
  * `timeout::Real=5.0`: タイムアウト（秒単位）で、これを過ぎると [`Timeout`](@ref) が返されます、
  * `kwargs...`: `full` または `timeout`。
