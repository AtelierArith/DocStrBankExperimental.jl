```julia
encrypt_caesar(plaintext, key::Integer)
encrypt_caesar(plaintext)
```

与えられた平文をシーザー暗号に従って暗号化します。キーは整数として与えられ、各文字のオフセットを示します。したがって、`encrypt_caesar("abc", 1) == "BCD"`です。

入力を大文字に変換しますが、記号は保持します。

伝統的に、シーザー暗号は3のシフトで使用されていたため、平文のみが与えられた場合はこのメソッドにフォールバックします。

---

### 例

```julia
julia> encrypt_caesar("Hello, World!", 3)
"KHOOR, ZRUOG!"
```
