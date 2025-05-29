```
localanisotropies(Gradients, grid, propname, w)
```

参照シナリオから `LocalAnisotropy` を抽出します。`grid` オブジェクトの直交座標系の `propname` 変数がスキャンされ、そこから局所的な勾配が抽出されます。これらの勾配は、2`w` x 2`w` (x 2`w`) のサイズの平方/立方ウィンドウ内で平滑化され、変動が大きい/小さい方向に沿った楕円/楕円体が返されます（`w` は `Int` 値であり、グリッドセルの数に対応します）。また、予備的な大きさも抽出され、後で [`rescale_magnitude`](@ref) 関数を使用して適切な範囲に再スケーリングできます。

## 例

```julia
lpars = localanisotropies(Gradients, grid, :CO2, 5)
```
