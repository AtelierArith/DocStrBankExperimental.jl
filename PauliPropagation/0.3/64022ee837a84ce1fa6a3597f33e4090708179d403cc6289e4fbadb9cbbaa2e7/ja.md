```
getcoeff(psum::PauliSum, pauli::Symbol, qind::Integer)
```

`PauliSum`内のパウリ文字列の係数を、量子ビット`qind`で作用するシンボルとしてパウリ文字列を提供することで取得します。これは、`add!()`を介してパウリ文字列が`PauliSum`に追加される方法と一致しています。`PauliSum`にパウリ文字列が存在しない場合は、デフォルトで0になります。
