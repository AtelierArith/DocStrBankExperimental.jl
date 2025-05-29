```
my_interpolate(arr, size_n, [interp_type])
```

`arr`を`size_n`で指定されたサイズに補間します。したがって、`ndims(arr) == length(size_n)`が成り立ちます。`interp_type`は補間の種類を指定します。すべてのオプションについてはInterpolations.jlを参照してください。
