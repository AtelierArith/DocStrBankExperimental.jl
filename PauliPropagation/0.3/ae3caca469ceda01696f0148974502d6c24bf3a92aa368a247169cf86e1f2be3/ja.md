```
getcoeff(psum::PauliSum, pstr::Vector{Symbol})
```

`PauliSum`内のパウリ文字列の係数を、すべてのキュービットに作用するシンボルのベクトルとしてパウリ文字列`pstr`を提供することで取得します。これは、`add!()`を介してパウリ文字列を`PauliSum`に追加する方法と一貫しています。`PauliSum`にパウリ文字列が存在しない場合は、デフォルトで0になります。
