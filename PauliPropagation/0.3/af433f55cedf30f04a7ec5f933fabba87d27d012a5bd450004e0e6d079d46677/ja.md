```
add!(psum1::PauliSum, psum2::PauliSum)
```

2つの`PauliSum`である`psum1`と`psum2`を加算します。`psum1`はその場で変更されます。`psum1`と`psum2`は同じ数のキュービットで定義されている必要があり、同じ係数型である必要があります。
