おそらく古典的な暗号の中で最も単純なもの、置換暗号は任意の置換辞書を作成することによって機能します。例えば、

```julia
'a' => 'x'
'b' => 'g'
'c' => 'l'
...
```

この辞書は、平文の入力における対応する文字を辞書の入力で指定された異なる文字に置き換えます。

関数 `decrypt_substitution` は、この辞書を第二のパラメータとして受け取るか、*または* 辞書自体を構築することができます：

```julia
decrypt_substitution(ciphertext, Dict(...); reverse_dict = true)
decrypt_substitution(ciphertext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true) # これは辞書 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' を作成します
decrypt_substitution(ciphertext, "zyxwvutsrqponmlkjihgfedcba"; reverse_dict = true) # これは置換辞書のキーを仮定して辞書 'a' => 'z', 'b' => 'y', ..., 'z' => 'a' を作成します
```

*辞書で未定義のすべての文字はデフォルトで保持されます。これには句読点、スペース、ケースが含まれます。* つまり、辞書を使用する場合、文字列は自動的に小文字に変換されません。

*`reverse_dict` が true に設定されている場合（デフォルトでそうなっています）、入力辞書は *en*crypt に使用されたものと同じであると見なされ、暗号文を *decrypt* するために逆転されます。*

慣例に従い、出力は常に小文字になります。

詳細については、[`https://en.wikipedia.org/wiki/Substitution_cipher`](https://en.wikipedia.org/wiki/Substitution_cipher) を参照してください。

---

### 例

```julia
julia> decrypt_monoalphabetic("ITSSG, ZIOL OL HSQOFZTBZ", "abcdefghijklmnopqrstuvwxyz", "qwertyuiopasdfghjklzxcvbnm", reverse_dict = true)
"hello, this is plaintext"

julia> decrypt_monoalphabetic("Khoor, Zruog!", "DEFGHIJKLMNOPQRSTUVWXYZABC")
"hello, world!"
```
