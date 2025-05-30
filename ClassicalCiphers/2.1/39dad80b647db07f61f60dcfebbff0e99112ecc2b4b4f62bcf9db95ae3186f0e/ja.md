```julia
encrypt_atbash(plaintext, alphabet)
```

置換暗号の特別なケースであるアトバッシュ暗号は、与えられたアルファベットをその逆に置き換えます：

```julia
encrypt_atbash(plaintext, "abcdefghijklmnopqrstuvwxyz") == encrypt_substitution(plaintext, "abcdefghijklmnopqrstuvwxyz", "zyxwvutsrqponmlkjihgfedcba")
```

*アルファベットを省略すると、英語のアルファベットを使用していると見なされます。*
