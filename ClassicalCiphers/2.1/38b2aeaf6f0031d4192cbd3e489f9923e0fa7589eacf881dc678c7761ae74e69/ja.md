```julia
crack_caesar(ciphertext; cleverness::Integer = 1)
```

与えられた暗号文をシーザー暗号に従って解読します。`encrypt_caesar(plaintext, key)` が暗号文を返すような `(plaintext, key::Integer)` を返します。

`cleverness=0` の場合、単に e の頻度を最大化するシフトを行います。`cleverness=1` の場合、文字列の総フィットネスを最大化します。

入力を小文字に変換します。

---

### 例

```julia
julia> crack_caesar("Khoor, Zruog!")
("hello, world!", 3)
```
