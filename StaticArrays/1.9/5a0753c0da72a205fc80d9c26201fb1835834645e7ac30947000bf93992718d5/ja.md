```
similar(static_array)
similar(static_array, T)
similar(array, ::Size)
similar(array, T, ::Size)
```

可変ですが静的サイズの配列（すなわち `StaticArray`）を構築して返します。入力の `array` が `StaticArray` でない場合、出力サイズを決定するために `Size` が必要です（さもなければ動的サイズの配列が返されます）。
