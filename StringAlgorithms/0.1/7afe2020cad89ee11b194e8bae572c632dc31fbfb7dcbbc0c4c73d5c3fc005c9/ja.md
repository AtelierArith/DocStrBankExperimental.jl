```julia
manacher(v)

```

グレン・K・マナッハによって1975年に提案されたマナッハアルゴリズム。

長さ `n` のベクトルが与えられると、各要素の間の間隔を含めると `2n+1` の位置が得られ、各位置で中心にある最長の回文を示す長さ `2n+1` のベクトルを返します。

# サンプル使用法

  * 最長の回文部分文字列の長さを見つける

```jldoctest
function longest_palindromic_substring(s)
    return maximum(manacher(s))
end

longest_palindromic_substring("ddabababacc")

# 出力

7
```
