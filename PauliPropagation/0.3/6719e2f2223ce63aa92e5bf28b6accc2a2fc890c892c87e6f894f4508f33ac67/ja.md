```
getcoeff(psum::PauliSum, pstr::Vector{Symbol}, qinds::Vector{Int})
```

`PauliSum`内のパウリ文字列の係数を、量子ビット`qinds`に作用するシンボルのベクトルとしてパウリ文字列`pstr`を提供することで取得します。これは、`add!()`を介してパウリ文字列を`PauliSum`に追加する方法と一致しています。`PauliSum`にパウリ文字列が存在しない場合は、デフォルトで0になります。
