```
str_detect(string::String, pattern::Union{String, Regex}; overlap::Bool=false)

                         文字列が特定のパターンを含むかどうかを判断します。
```

# 引数

  * `string`: チェックする文字列。
  * `pattern`: 文字列内で見つけるための文字列または正規表現。
  * `overlap`: パターンが重複できるかどうか（デフォルトはfalse）

パターンには特別なロジックを含めることができます：

```
                         | を使用して「または」を表します（例："red|blue"は"red"または"blue"を含む任意の文字列に一致します）。
                         & を使用して「かつ」を表します（例："red&blue"は"red"と"blue"の両方を含む任意の文字列に一致します）。
                         戻り値
                         文字列がパターンを含む場合はtrue、そうでない場合はfalse。
                         # 例
                         ```jldoctest
                         julia> str_detect("The sky is blue", "blue")
                         true

                         julia> str_detect("The sky is blue", "red")
                         false

                         julia> str_detect("The sky is blue", r"blu")
                         false

                         julia> str_detect("The sky is blue", "blue|red")
                         true

                         julia> str_detect("The sky is blue and the sun is red", "blue&red")
                         true
                         ```
```
