```
get_window(A::TiledView; window_function=window_hanning, get_norm=false, verbose=false, offset = CtrFT);
```

`TiledView`に一致するウィンドウを計算します。

`window_function`。`TiledView`に適用するためにIndexFunArraysで定義されたウィンドウ関数。結果は現在、乗算をビューにラップする方法が不明なため、もはやビューではありません。この理由から、ウィンドウが適用されていないTiledViewも返され、代入に使用できます。デフォルトでは、von Hannウィンドウ（window_hanning）が使用されます。偶数サイズの場合、ウィンドウは中央位置の右側の整数座標に中心が置かれます（`CtrFT`）。

`get_norm`。オプションのブール引数で、すべての必要なウィンドウ操作を受けない可能性のあるボーダーピクセルの正規化マップも取得できるようにします。将来のバージョンでは、この効果を回避できるようにウィンドウ配置を自動的に行うことが可能になるかもしれません。

`verbose`。trueの場合、ウィンドウレイアウトに関する診断情報が印刷されます。

`offset`。ウィンドウの中心が配置される場所を定義します。詳細については`IndexFunArrays.jl`を参照してください。

# 返り値

`matching_window`。ビューに対して乗算を介して適用できるウィンドウ myview.*matching_window これは、書き込みアクセスに関して概念的に機能を分離するために意図的に製品として提供されていません。

`normalized`。get_norm=trueの場合のみ返されます。ウィンドウを元のデータに戻すことによって正規化情報を含む配列です。これは、タイルの不完全なカバレッジや、タイル処理中に合計が1にならないウィンドウを使用する際に便利です。

# 例

```jldoctest
julia> data = ones(10,10).+0.0;

julia> myview = TiledView(data, (5, 5), (2,2));

julia> win = get_window(myview, verbose=true);
[ Info: Tiles with pitch (3, 3) overlap by (2, 2) pixels.
[ Info: Window starts at (0.5, 0.5) and ends at (2.5, 2.5).

julia> win
5×5 IndexFunArrays.IndexFunArray{Float64, 2, IndexFunArrays.var"#360#362"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.0214466  0.125     0.146447  0.125     0.0214466
 0.125      0.728553  0.853553  0.728553  0.125
 0.146447   0.853553  1.0       0.853553  0.146447
 0.125      0.728553  0.853553  0.728553  0.125
 0.0214466  0.125     0.146447  0.125     0.0214466

```

TiledWindowView()の詳細な例については、こちらを参照してください。
