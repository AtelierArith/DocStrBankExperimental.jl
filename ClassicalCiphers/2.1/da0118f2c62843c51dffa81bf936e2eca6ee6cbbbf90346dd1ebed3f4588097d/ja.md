```julia
decrypt_affine(ciphertext, mult::Integer, add::Integer; offset::Integer=0)
```

与えられた暗号文をアフィン暗号に従って復号化します。キーは整数のペアとして与えられます：最初が乗数、次が加算定数です。

乗数は26と互いに素でなければなりません。そうでない場合は、エラーが発生します。

入力を小文字に変換しますが、記号は保持します。

オプションの引数：`offset=0`、これは'a'がどの数値として考慮されるべきかを指定します。

---

### 例

```julia
julia> decrypt_affine("ZQLLU, SUDLN!", 3, 4)
"hello, world!"
```
