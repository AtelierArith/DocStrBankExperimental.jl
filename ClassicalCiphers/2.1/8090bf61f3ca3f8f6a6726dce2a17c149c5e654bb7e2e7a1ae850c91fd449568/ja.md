```julia
encrypt_affine(plaintext, mult::Integer, add::Integer; offset::Integer = 0)
```

与えられた平文をアフィン暗号に従って暗号化します。キーは整数のペアとして与えられます：最初が乗数、次が加算定数です。

乗数は26と互いに素でなければなりません。そうでない場合、エラーが発生します。

入力を大文字に変換しますが、記号は保持されます。

オプションの引数：`offset=0`、これは'a'がどの数値として考慮されるべきかを指定します。

---

### 例

```julia
julia> encrypt_affine("Hello, World!", 3, 4)
"ZQLLU, SUDLN!"
```
