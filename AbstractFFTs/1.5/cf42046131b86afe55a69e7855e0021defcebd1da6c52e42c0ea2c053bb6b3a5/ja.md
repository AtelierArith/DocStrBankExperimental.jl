```
ifftshift(x, [dim])
```

与えられた次元に沿って、インデックス `N÷2+1` に中心を置いた周期信号 `x` を円形シフトし、インデックス `1` に中心を置くようにします。ここで、`N` はその次元のサイズです。

これは [`fftshift`](@ref) の効果を元に戻します。偶数の `N` の場合、これは最初の半分と第二の半分を入れ替えることに相当するため、[`fftshift`](@ref) と `ifftshift` は同じです。

`dim` が指定されていない場合、信号は各次元に沿ってシフトされます。

`ifftshift` の出力は割り当てられます。出力を事前に割り当てられた配列に保存したい場合は、代わりに [`ifftshift!`](@ref) を使用してください。
