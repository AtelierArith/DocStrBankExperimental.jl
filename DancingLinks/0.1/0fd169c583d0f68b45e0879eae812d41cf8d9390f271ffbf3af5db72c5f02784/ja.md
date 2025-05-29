```
    convert_nanoseconds(nanosecs::UInt64; # time_ns() 関数から
                    [ncols]::Integer = 0, # < 0 = 先頭のゼロ値を破棄; 最も重要な列を最初に表示 (以下の例を参照)
                    [units]::Union{Nothing, Symbol}=nothing,  # != nothing : 例. :ms; 最後の列はこれらの単位
                                                            # そうでなければ最後の列は任意の単位
                                                            # units = :d, :h, :m, {:s|:sec}, :ms, {:mus|μs}, :ns
                    [omitunits]::Bool=false # 単位文字列を表示するかどうか
                    )::String
```

この関数は、例えば `time_ns()` と一緒に使用されます。

# 例

```
t = 1.500600e9 # ナノ秒
convert_nanoseconds(t, ncols = 0, units=nothing)   -> "01:500:600μs"
convert_nanoseconds(t, ncols = +1, units=nothing)  -> "1500600μs"
convert_nanoseconds(t, ncols = -1, units=nothing)  -> "2s"
convert_nanoseconds(t, ncols = +2, units=nothing)  -> "1500:600μs"
convert_nanoseconds(t, ncols = -2, units=nothing)  -> "01:501ms"
convert_nanoseconds(t, ncols = +3, units=:ms)      -> "00:01:501ms"
convert_nanoseconds(t, ncols = -3, units=:ms)      -> "01:501ms"
```
