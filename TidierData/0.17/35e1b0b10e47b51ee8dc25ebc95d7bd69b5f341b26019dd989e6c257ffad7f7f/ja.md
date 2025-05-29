```
is_number(column::AbstractVector)
```

与えられた列が数値を含むかどうかを判断します。

# 引数

  * `column::AbstractVector`: データ型をチェックする必要がある列。

# 戻り値

  * `Bool`: 列が数値を含む場合は `true`、そうでない場合は `false`。

# 例

```jldoctest
julia> df = DataFrame(b = [missing, 2, 3],
                      c = [missing, 2.2, 34],
                      d = [missing, missing, "A"]);

julia> is_number(df.b)
true

julia> is_number(df.c)
true

julia> is_number(df.d)
false
```
