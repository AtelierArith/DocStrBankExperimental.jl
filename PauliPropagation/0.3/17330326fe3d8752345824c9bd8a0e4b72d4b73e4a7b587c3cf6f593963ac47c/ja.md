```
add!(psum::PauliSum{TermType, CoeffType}, pstr::TermType, coeff::CoeffType)
```

Pauli文字列`pstr`を係数`coeff`とともに`PauliSum` `psum`に追加します。これは`psum`をインプレースで変更します。`pstr`は`paulitype(psum)`と同じ型である必要があり、`coeff`は`coefftype(psum)`と同じ型である必要があります。
