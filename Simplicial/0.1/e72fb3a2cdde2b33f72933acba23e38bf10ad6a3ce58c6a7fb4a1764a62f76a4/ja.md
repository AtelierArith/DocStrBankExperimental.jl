```
matrix_form(C::CombinatorialCode)
```

コードの `BitMatrix` 表現で、行はコードワードです。返されるコードワードの順序は `C.words` の順序と一致します。誰も `C` のフィールドをいじっていないと仮定すると、これらは `lessequal_GrRevLex` を使用してソートされているはずです。
