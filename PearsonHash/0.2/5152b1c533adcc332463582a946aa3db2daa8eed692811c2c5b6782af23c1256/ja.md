```
hashn([T = UInt128], data; seed::UInt8 = zero(UInt8))::T where T
```

`Vector{UInt8}(data)`のために`(8*n)`ビットのハッシュを計算します。ここで、`n == sizeof(T)`（オプションで`seed`を指定できます）。*注意:* `data`は変更を防ぐためにコピーされます（結果として追加のアロケーションが発生します）。
