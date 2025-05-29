```
@deparse expr
```

`expr`から文字列を作成します。Julia REPLで入力するのと似たような出力を試みます。`expr`に`@comment <message>`が含まれている場合、それは`# <message>`に変換されます。

# 例

```jldoctest
julia> @deparse 1+1
"1 + 1"

julia> @deparse sin(1f0+a)
"sin(1.0f0 + a)"

julia> @deparse f(x) = sin(x)/x  # 期待通りに動作しないことがあります
"f(x) = begin\n        sin(x) / x\n    end\n"
```
