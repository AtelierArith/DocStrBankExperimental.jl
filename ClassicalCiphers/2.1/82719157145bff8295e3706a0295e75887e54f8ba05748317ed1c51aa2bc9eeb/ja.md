```julia
decrypt_caesar(ciphertext, key::Integer)
decrypt_caesar(ciphertext)
```

与えられた暗号文をシーザー暗号に従って復号化します。キーは整数として与えられ、各文字のオフセットを示します。したがって、`decrypt_caesar("abcd", 1) == "zabc"`です。

入力を小文字に変換しますが、記号は保持します。

伝統的に、シーザー暗号は3のシフトで使用されていたため、平文のみが与えられた場合はこのメソッドにフォールバックします。

---

### 例

```julia
julia> decrypt_caesar("Khoor, Zruog!", 3)
"hello, world!"
```
