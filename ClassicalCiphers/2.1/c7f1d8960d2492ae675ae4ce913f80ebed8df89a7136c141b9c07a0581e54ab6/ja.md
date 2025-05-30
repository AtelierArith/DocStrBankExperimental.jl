おそらく古典的な暗号の中で最も単純なもの、置換暗号は任意の置換辞書を作成することによって機能します。例えば、

```julia
'a' => 'x'
'b' => 'g'
'c' => 'l'
...
```

この辞書は、平文の入力における対応する文字を辞書の入力で指定された異なる文字に置き換えます。

関数 `encrypt_substitution` は、この辞書を第二のパラメータとして受け取るか、*または* 自身で辞書を構築することができます：

```julia
encrypt_substitution(plaintext, Dict(...))
encrypt_substitution(plaintext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba") # これにより辞書 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' が作成されます
encrypt_substitution(plaintext, "zyxwvutsrqponmlkjihgfedcba") # これにより置換辞書のキーを仮定して辞書 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' が作成されます
```

*辞書に定義されていないすべての文字はデフォルトで保持されます。これには句読点、スペース、ケースが含まれます。* つまり、辞書を使用する際、文字列は自動的に大文字に変換されるわけではありません。

慣例に従い、出力は常に大文字になります。

詳細については、[`https://en.wikipedia.org/wiki/Substitution_cipher`](https://en.wikipedia.org/wiki/Substitution_cipher)を参照してください。

---

### 例

```julia
julia> encrypt_monoalphabetic("Hello, World!", "DEFGHIJKLMNOPQRSTUVWXYZABC")
"KHOOR, ZRUOG!"

julia> encrypt_monoalphabetic("aBcbDd", Dict{Char, Char}('a' => '5', 'B' => '@', 'b' => 'o'))
"5@coDd"

julia> encrypt_monoalphabetic("Hello, this is plaintext", "abcdefghijklmnopqrstuvwxyz", "qwertyuiopasdfghjklzxcvbnm")
"ITSSG, ZIOL OL HSQOFZTBZ"

julia> encrypt_monoalphabetic("Hello, this is plaintext", "qwertyuiopasdfghjklzxcvbnm")
"ITSSG, ZIOL OL HSQOFZTBZ"

julia> encrypt_monoalphabetic("xyz", Dict('x' => 'd', 'y' => 'e', 'z' => 't'))
"det"
```
