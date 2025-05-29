```
HrseReadOptions(kwargs...)
```

HRSEファイルを解析するためのオプションを格納します。

# 引数

  * `integertypes = [Int64, BigInt]`: 整数を解析するために試す符号付き整数型のリスト。整数を表現できる最初の型が使用されます。
  * `floattype = Float64`: 浮動小数点数を解析するための浮動小数点型。
  * `readcomments = false`: コメントを読み取り、`CommentedElement`オブジェクトに格納するかどうか; falseの場合、コメントは無視されます。
  * `extensions`: HRSEへの[`Extension`](@ref)のコレクション。

また、[`readhrse`](@ref)も参照してください。
