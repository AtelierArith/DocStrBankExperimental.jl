```
sparse_matrix_form(C::CombinatorialCode)
```

`C`の`Bool`エントリを持つ`SparseMatrixCSC`表現; 行はコードワードとして。

返されるコードワードの順序は`C.words`の順序と一致します。誰も`C`のフィールドをいじっていないと仮定すると、これらは`lessequal_GrRevLex`を使用してソートされているはずです。
