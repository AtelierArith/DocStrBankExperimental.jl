```julia
crack_affine(ciphertext; mult::Integer = 0, add::Integer = -1)
```

与えられた暗号文をアフィン暗号に従って解読します。`((乗数, 加算定数), 復号化された文字列)`を返します。

入力を小文字に変換しますが、記号は保持します。

オプションの引数: `mult=0`は、既知の場合の乗数を指定します; `add=-1`は、既知の場合の加算定数を指定します。

---

### 例

```julia
julia> crack_affine("ZQLLU, SUDLN!")
("hello, world!", (3, 4))
```
