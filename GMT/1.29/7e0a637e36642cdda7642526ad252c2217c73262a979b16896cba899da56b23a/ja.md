```
buffergeo(D::GMTdataset; width=0, unit=:m, np=120, flatstart=false, flatend=false, epsg::Integer=0, tol=0.01)
```

または

```
buffergeo(line::Matrix; width=0, unit=:m, np=120, flatstart=false, flatend=false, proj::String="", epsg::Integer=0, tol=0.01)
```

または

```
buffergeo(fname::String; width=0, unit=:m, np=120, flatstart=false, flatend=false, proj::String="", epsg::Integer=0, tol=0.01)
```

ポリラインの周りにバッファを計算します。この計算は、GeographicLib（PROJ4経由）を使用して楕円体の地球（または他の惑星）上で行われるため、非常に正確です。

### パラメータ

  * `D` | `line` | fname: - ジオメトリ。この値はGMTdataset（またはそのベクトル）、Mx2行列、`gmtread()`でGMTdatasetとして読み取ることができるファイルの名前、またはGDAL AbstractDatasetオブジェクトのいずれかです。
  * `width`:  - 適用されるバッファ幅。メートル（デフォルト）、km、またはマイルで表現されます（`unit`を参照）。
  * `unit`:   - `width`がメートルでない場合は、`unit=:km`、`unit=:Nautical`、または`unit=:Miles`のいずれかを使用します。
  * `np`:     - 円を離散化するためのポイント数（デフォルト = 120）。
  * `flatstart` - ポリラインの周りにバッファを計算する際に、開始を*フラット*にします（半円なし）。
  * `flatend`   - バッファの終了に対して`flatstart`と同じ。
  * `proj`  - 線データが直交座標系にあるが、既知の投影がある場合は、バッファ計算を可能にするためにPROJ4文字列を渡します。
  * `epsg`  - `proj`と同じですが、EPSGコードを使用します。
  * `tol`   - 最後にダグラス-ピーカー法を使用してバッファラインを簡略化します。ラインの簡略化を行わない場合はTOL=0を使用するか、他の任意の値（度単位）を使用します。デフォルトでは、バッファ幅の0.5%として計算されます。

### 戻り値

GMTデータセットまたはそのベクトル（入力がVector{GMTdataset}の場合）。

## 例: 幅50000 mのバッファを計算する

```
D = buffergeo([0 0; 10 10; 15 20], width=50000);
```
