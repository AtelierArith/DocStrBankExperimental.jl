```
angles, ind = vecangles(lonlat0::VecOrMat{Real}, lonlat1::Matrix{Real}; proj::String="",
                        s_srs::String="", epsg::Integer=0, sorted=true)
```

中央点 `lonlat0` から引いた線と Mx2 行列 `lonlat1` に渡された線との間の角度を計算します。

引数:

  * `lonlat1`:  - 指定された投影における点1の座標（または複数の点を持つ行列）。
  * `lonlat2`:  - 指定された投影における点2の座標（または `lonlat1` と同じサイズの行列）。
  * `proj` または `s_srs`:  - 移動する楕円体を持つ指定された投影。proj4 文字列または WKT であることができます。
  * `epsg`:     - 投影を指定する別の方法 [デフォルトは WGS84]。
  * `sorted`:   - デフォルトでは、線の方位をソートして角度が隣接する線に関連付けられるようにします。`sorted` が `false` に設定されている場合、`lonlat2` に与えられた点の順序で角度を計算します。

### 戻り値

  * `angles` - 引数によって決定された中心と点の間の角度を持つ Float64 ベクトル、さらに中心から最初の点および中心から最後の点への線の間の角度も含まれます。
  * `ind` - 線の方位をソートすることによって得られた順序の Int ベクトル（`sorted=true` の場合）。これを `lonlat2[ind,:]` に適用して、`angles` と同じ方法で点の分布順序を取得します。もちろん、`sorted=false` の場合は必要ありません。
