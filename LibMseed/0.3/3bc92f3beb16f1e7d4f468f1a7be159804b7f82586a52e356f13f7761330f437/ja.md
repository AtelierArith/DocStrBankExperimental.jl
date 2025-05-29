```
NanosecondDateTime(nstime)
```

`Int64`から`NanosecondDateTime`を構築します。これは、エポック`1970-01-01T00:00:00.000000000`からのナノ秒の整数値を表します。したがって、表現可能な日付の範囲は`1677-09-21T00:12:43.145224192 - 2262-04-11T23:47:16.854775807`です。

# 例

```
julia> NanosecondDateTime(100)
NanosecondDateTime("1970-01-01T00:00:00.000000100")
```
